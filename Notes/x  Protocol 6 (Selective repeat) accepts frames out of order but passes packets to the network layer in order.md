```c
/* Protocol 6 (Selective repeat) accepts frames out of order but passes packets to the network layer in order. Associated with each outstanding freme is a timer. When the timer expires, only that frame is retransmitted, not all the outstanding frames, as in protocol 5. */
#define MAX_SEQ 7		    /* should be 2^n-1   */
#define NR_BUFS((MAX_SEQ + 1)/2)
typedef enum{
  frame_arraival, 
  cksum_err,
  timeout,
  network_layer_ready,
  ack_timeout
} event_type;

#include "protocol.h"
boolean no_nak = true; /*no nak has been sent yet*/
seq_nr oldest_frame = MAX_SEQ + 1; /*initial value is only for the simulator*/

static boolean between(seq_nr a, seq_nr b, seq_nr c){
  /*Same as between in protocol 5, but shorter and more obscure.*/ 
  return ((a <= b) && (b < c)) || ((c < a) && (a <= b)) || ((b < c) && (c < a)); 
}

static void send frame(frame_kind fk, seq_nr frame_nr, seq_nr frame_expected, packet buffer[]){
  /*Construct and send a data, ack, or nak frame.*/
  frame s; /*scratch var iable*/
  s.kind = fk; /*kind == data, ack, or nak*/
  if (fk == data) {
    s.info = buffer[frame_nr % NR_BUFS];
  }
  s.seq = frame_nr ; /*only meaningful for data frames*/
  s.ack = (frame_expected + MAX_SEQ) % (MAX_SEQ + 1);
  
  if (fk == nak) {
    no_nak = false; /*one nak per frame, please*/
  }
  to_physical_layer(&s); /*transmit the frame*/
  if (fk == data) {
    start_timer(frame_nr % NR_BUFS); 
    stop_ack_timer(); /*no need for separate ack frame*/ 
  }
}

void protocol6(void) { 
  seq_nr ack_expected; /*lower edge of sender’s window*/ 
  seq_nr next_frame_to_send; /*upper edge of sender’s window + 1*/ 
  seq_nr frame_expected; /*lower edge of receiver’s window*/ 
  seq_nr too_far; /*upper edge of receiver’s window + 1*/ 
  int i; /*index into buffer pool*/ 
  frame r; /*scratch var iable*/ 
  packet out_buf[NR_BUFS]; /*buffers for the outbound stream*/ 
  packet in_buf[NR_BUFS]; /*buffers for the inbound stream*/ 
  boolean arrived[NR_BUFS]; /*inbound bit map*/ 
  seq_nr nbuffered; /*how many output buffers currently used*/ 
  event_type event; 
  enable_network_layer(); /*initialize*/ 
  ack_expected = 0; /*next ack expected on the inbound stream*/ 
  next_frame_to_send = 0; /*number of next outgoing frame*/ 
  frame_expected = 0; 
  too_far = NR_BUFS; 
  nbuffered = 0; /*initially no packets are buffered*/ 
  for (i = 0; i < NR BUFS; i++) arrived[i] = false; 
  while (true) { 
    wait for event(&event); /*five possibilities: see event type above*/
    switch(event) { 
      case network_layer_ready: /*accept, save , and transmit a new frame*/ 
        nbuffered = nbuffered + 1; /*expand the window*/ 
        from_network_layer(&out_buf[next_frame_to_send % NR_BUFS]); /*fetch new packet*/ 
        send_frame(data, next_frame_to_send, frame_expected, out_buf);/*transmit the frame*/ 
        inc(next_frame_to_send); /*advance upper window edge*/ 
        break; 
      case frame_arrival: /*a data or control frame has arrived*/ 
        from_physical_layer(&r); /*fetch incoming frame from physical layer*/ 
        if (r.kind == data) { 
          /*An undamaged frame has arrived.*/ 
          if ((r.seq != frame_expected) && no_nak) 
            send_frame(nak, 0, frame_expected, out_buf); 
          else start_ack_timer(); 
          if (between(frame_expected,r.seq,too_far) && (arrived[r.seq%NR_BUFS]==false)) { 						/*Frames may be accepted in any order.*/ 
            arrived[r.seq % NR_BUFS] = true; /*mar k buffer as full*/ 
            in_buf[r.seq % NR_BUFS] = r.info; /*inser t data into buffer*/ 
            while (arrived[frame_expected % NR_BUFS]) { 
              /*Pass frames and advance window.*/ 
              to_network_layer(&in_buf[frame_expected % NR_BUFS]); 
              no_nak = true; 
              arrived[frame_expected % NR_BUFS] = false; 
              inc(frame_expected); /*advance lower edge of receiver’s window*/ 
              inc(too_far); /*advance upper edge of receiver’s window*/ 
              start_ack_timer(); /*to see if a separate ack is needed*/ 
            } 
          } 
        } 
        if((r.kind==nak) && between(ack_expected,(r.ack+1)%(MAX SEQ+1),next_frame_to_ send)) send_frame(data, (r.ack+1) % (MAX_SEQ + 1), frame_expected, out_buf); 
        while (between(ack_expected, r.ack, next_frame_to_send)) { 
          nbuffered = nbuffered - 1; /* handle piggybacked ack */ 
          stop_timer(ack_expected % NR_BUFS); /*frame arrived intact*/ 
          inc(ack_expected); /*advance lower edge of sender’s window*/ 
        } break; 
      case cksum_err : 
        if (no_nak) send_frame(nak, 0, frame_expected, out_buf); /*damaged frame*/ 
        break; 
      case timeout: send_frame(data, oldest_frame, frame_expected, out_buf); /*we timed out*/ 
        break; 
      case ack_timeout: 
        send_frame(ack,0,frame_expected, out_buf); /*ack timer expired; send ack*/ 
    } if (nbuffered < NR_BUFS) 
      enable_network_layer(); 
    else 
      disable networ k layer(); 
  } 
}
```



If the else clause were omitted, this change will affect the protocol's correctness.

```c
      case frame_arrival: /*a data or control frame has arrived*/ 
        from_physical_layer(&r); /*fetch incoming frame from physical layer*/ 
        if (r.kind == data) { 
          /*An undamaged frame has arrived.*/ 
          if ((r.seq != frame_expected) && no_nak) 
            send_frame(nak, 0, frame_expected, out_buf); 
          else start_ack_timer(); 
          if (between(frame_expected,r.seq,too_far) && (arrived[r.seq%NR_BUFS]==false)) { 						/*Frames may be accepted in any order.*/ 
            arrived[r.seq % NR_BUFS] = true; /*mar k buffer as full*/ 
            in_buf[r.seq % NR_BUFS] = r.info; /*inser t data into buffer*/ 
            while (arrived[frame_expected % NR_BUFS]) { 
              /*Pass frames and advance window.*/ 
              to_network_layer(&in_buf[frame_expected % NR_BUFS]); 
              no_nak = true; 
              arrived[frame_expected % NR_BUFS] = false; 
              inc(frame_expected); /*advance lower edge of receiver’s window*/ 
              inc(too_far); /*advance upper edge of receiver’s window*/ 
              start_ack_timer(); /*to see if a separate ack is needed*/ 
            } 
          } 
        } 
```



```c
      case frame_arrival: /*a data or control frame has arrived*/ 
        from_physical_layer(&r); /*fetch incoming frame from physical layer*/ 
        if (r.kind == data) { 
          /*An undamaged frame has arrived.*/ 
          if ((r.seq != frame_expected) && no_nak) 
            send_frame(nak, 0, frame_expected, out_buf);
          if (between(frame_expected,r.seq,too_far) && (arrived[r.seq%NR_BUFS]==false)) { 						/*Frames may be accepted in any order.*/ 
            arrived[r.seq % NR_BUFS] = true; /*mar k buffer as full*/ 
            in_buf[r.seq % NR_BUFS] = r.info; /*inser t data into buffer*/ 
            while (arrived[frame_expected % NR_BUFS]) { 
              /*Pass frames and advance window.*/ 
              to_network_layer(&in_buf[frame_expected % NR_BUFS]); 
              no_nak = true; 
              arrived[frame_expected % NR_BUFS] = false; 
              inc(frame_expected); /*advance lower edge of receiver’s window*/ 
              inc(too_far); /*advance upper edge of receiver’s window*/ 
              start_ack_timer(); /*to see if a separate ack is needed*/ 
            } 
          } 
        } 
```

If the frame is not expected frame and `no_nak == true`, it will send the run ` send_frame(nak, 0, frame_expected, out_buf);`  else has three situations:

1. `r.seq != frame_expected && no_nak == false`
2. `r.seq == frame_expected && no_nak == false`
3. `r.seq == frame_expected && no_nak == true`

It might lead to deadlock. For these three situations, the receiver will send acknowledgements to the sender. If the  acknowledgements were lost. The receiver will not realize that. But the sender realize it does not get the acknowledgement, it will resend the first frame again. But at this time the `r.seq != frame_expected && no_nak==true `.  The receiver will always run ` send_frame(nak, 0, frame_expected, out_buf); `  And then the sender and will keep send the same frame again and again. The whole process will stuck here. 

Therefore it is necessary to set the auxiliary timer which can result in a correct acknowledgement being sent back eventually instead, which resynchronizes.







Then it will go in to the ` send_frame(nak, 0, frame_expected, out_buf);` , the receiver will send NAK. The send will send the thing again. But the receiver has already accepted. 



for the second it will always waiting for the `no`



1. Yes. It might lead to deadlock. Suppose that a batch of frames arrived correctly and was accepted. The receiver would advance its window. Now suppose that all the acknowledgements were lost. The sender would eventually time out and send the first frame again. The receiver would then send a NAK. If this packet were lost, from that point on, the sender would keep timing out and sending a frame that had already been accepted, but the receiver would just ignore it. Setting the auxiliary timer results in a correct acknowledgement being sent back eventually instead, which resynchronizes.
2. It would lead to deadlock because this is the only place that incoming acknowledgements are processed. Without this code, the sender would keep timing out and never make any progress.







```
      case frame_arrival: /*a data or control frame has arrived*/ 
        from_physical_layer(&r); /*fetch incoming frame from physical layer*/ 
        if (r.kind == data) { 
          /*An undamaged frame has arrived.*/ 
          if ((r.seq != frame_expected) && no_nak) 
            send_frame(nak, 0, frame_expected, out_buf); 
          else start_ack_timer(); 
          if (between(frame_expected,r.seq,too_far) && (arrived[r.seq%NR_BUFS]==false)) { 						/*Frames may be accepted in any order.*/ 
            arrived[r.seq % NR_BUFS] = true; /*mar k buffer as full*/ 
            in_buf[r.seq % NR_BUFS] = r.info; /*inser t data into buffer*/ 
            while (arrived[frame_expected % NR_BUFS]) { 
              /*Pass frames and advance window.*/ 
              to_network_layer(&in_buf[frame_expected % NR_BUFS]); 
              no_nak = true; 
              arrived[frame_expected % NR_BUFS] = false; 
              inc(frame_expected); /*advance lower edge of receiver’s window*/ 
              inc(too_far); /*advance upper edge of receiver’s window*/ 
              start_ack_timer(); /*to see if a separate ack is needed*/ 
            } 
          } 
        } 
        if((r.kind==nak) && between(ack_expected,(r.ack+1)%(MAX SEQ+1),next_frame_to_ send)) send_frame(data, (r.ack+1) % (MAX_SEQ + 1), frame_expected, out_buf); 
        while (between(ack_expected, r.ack, next_frame_to_send)) { 
          nbuffered = nbuffered - 1; /* handle piggybacked ack */ 
          stop_timer(ack_expected % NR_BUFS); /*frame arrived intact*/ 
          inc(ack_expected); /*advance lower edge of sender’s window*/ 
        } break; 
```

