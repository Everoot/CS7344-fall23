# Midterm Questions

## Questions:

1. What is Subnet?

   A subnet (subnetwork) is a logical subdivision of an IP network. It is used to divide a large network into smaller, more manageable pieces to improve network performance and security. The subnet is identified by its subnet mask, which determines which IP addresses are included in that subnet.

   子网（Subnet）是IP网络的逻辑细分。它用于将大型网络划分为更小、更易于管理的片段，以改善网络性能和安全性。子网由子网掩码标识，子网掩码决定了该子网中包含哪些IP地址。

2. What are the differences between large wired LANs vs WAN?

   - **LAN (Local Area Network):** 

     **局域网 (LAN，Local Area Network)：**

     - Covers a small geographic area, like a home, office, or campus. 

       覆盖小的地理区域，如家庭、办公室或校园。

     - Typically high data transfer rates.

       通常有高数据传输速率。

     - Primarily uses Ethernet and Wi-Fi technologies.

       主要使用以太网和Wi-Fi技术。

     - Privately owned and managed.

       私人拥有和管理。

   - **WAN (Wide Area Network):**

     - Covers a large geographic area, potentially global.

       覆盖大的地理区域，可能是全球范围。

     - Lower data transfer rates compared to LANs.

       与局域网相比，数据传输率较低。

     - Uses technologies like MPLS, Frame Relay, and X.25.

       使用技术如MPLS、帧中继和X.25。

     - Can be privately owned or leased.

       可以是私人拥有或租赁

3. What is VPN?

   A Virtual Private Network (VPN) is a technology that creates a secure and encrypted connection over a less secure network, such as the Internet. It allows users to securely access a private network and share data remotely through public networks.

   虚拟专用网络（VPN，Virtual Private Network）是一种创建在不太安全的网络，如互联网上的安全和加密连接的技术。它允许用户通过公共网络安全地访问私有网络，并远程共享数据。

4. How NSFNET works?

   The National Science Foundation Network (NSFNET) was a program of coordinated, evolving projects sponsored by the National Science Foundation (NSF) beginning in 1985 to promote advanced research and education networking in the United States. It played a significant role in the development of the modern internet by connecting various regional networks and was a precursor to the global Internet.

   国家科学基金网络（NSFNET）是国家科学基金会（NSF）从1985年开始赞助的一系列协调、发展中的项目，旨在推动美国的高级研究和教育网络。通过连接各种区域网络，它在现代互联网的发展中发挥了重要作用，并是全球互联网的前身。

5. How do you get network connection at your home?

   Typically, you get a network connection at your home by subscribing to an Internet Service Provider (ISP). The ISP provides the necessary equipment, like a modem and/or router, and establishes a connection either via cable, DSL, fiber-optic, satellite, or cellular networks, depending on the available technology in your area.

   通常，您可以通过订阅互联网服务提供商（ISP）在家中获取网络连接。ISP提供必要的设备，如调制解调器和/或路由器，并通过有线、DSL、光纤、卫星或蜂窝网络建立连接，具体取决于您所在地区的可用技术。



6. Difference between Baseband and Passband Transmission?

   - **Baseband Transmission:**

     **基带传输：**

     - Sends digital signals directly over the medium without modulating them to different frequencies.

       直接在媒介上发送数字信号，不对它们进行调制至不同频率。

     - Typically used in LANs.

       通常用于局域网。

   - **Passband Transmission:**

     **通带传输**

     - Modulates digital or analog signals to higher frequencies suitable for transmission.

       将数字或模拟信号调制至更高的频率以适合传输。

     - Used in situations where the medium is shared, like radio or satellite communication.

       用于媒介共享的情况，如无线电或卫星通信。

7. How FDM works?

   - **FDM (Frequency Division Multiplexing):**

     **频分复用 (FDM)：**

     - Divides the available bandwidth into different frequency bands, each assigned to a different channel.

       将可用带宽划分为不同的频带，每个频带分配给一个不同的信道。

8. How TDM works?

   - **TDM (Time Division Multiplexing):**

     时分复用 (TDM)：

     - Allocates time slots to each channel in a cyclic manner.

       以循环方式为每个信道分配时隙。

9. How CDM works?

   - **CDM (Code Division Multiplexing):**

     **码分复用 (CDM)：**

     - Allocates a unique code to each channel so that multiple channels can be transmitted simultaneously over the same frequency.

       为每个信道分配唯一的代码，以便多个信道可以同时在同一频率上传输。

10. How WDM works?

    - **WDM (Wavelength Division Multiplexing):**

      **波分复用 (WDM)：**

      - Used in fiber-optic communication, where different channels are transmitted at different wavelengths (colors) of light.

        用于光纤通信，其中不同信道以不同波长（颜色）的光传输。

11. Why is Cellular Network called cellular?

    It is called "cellular" because it is made up of many small geographical areas or "cells." Each cell has its own base station allowing for connections within that cell.

    蜂窝网络之所以被称为“蜂窝”，是因为它由许多小的地理区域或“小区”组成。每个小区都有自己的基站，允许在该小区内进行连接。

12. Major differences among 1G, 2G, 3G, 4G, 5G

    - **1G:**

      - Analog transmission.

        模拟传输。

      - Voice-only communication.

        仅支持语音通信。

    - **2G:**

      - Digital transmission.

        数字传输。

      - upports voice and limited data services, like SMS and MMS.

        支持语音和有限的数据服务，如短信和彩信。

    - **3G:**

      - Enhanced data transfer rates.

        增强数据传输率。

      - Supports video calling and mobile internet.

        支持视频通话和移动互联网。

    - **4G:**

      - High-speed data access.

        高速数据访问。

      - Supports all IP-based services.

        支持所有基于IP的服务。

    - **5G:**

      - extremely high data rates and low latency.

        极高的数据传输率和低延迟。

      - Supports a variety of services like IoT, autonomous vehicles, etc.

        支持各种服务，如物联网、自动驾驶汽车等。

13. How satellite transmits data?

    Satellites transmit data using radio waves. Ground stations send signals to the satellite, which then transmits the signals back to the earth to another ground station.

    卫星使用无线电波传输数据。地面站向卫星发送信号，然后卫星将信号传回地球到另一个地面站。



14. Difference between packet and frame?

    - **Packet:**

      **分组：**

      - A packet is a formatted unit of data carried by a packet-switched network.

        分组是由分组交换网络携带的格式化数据单元。

      - It contains the payload and various control information including source and destination addresses.

        它包含载荷和各种控制信息，包括源和目的地地址。

    - **Frame:**

      **帧：**

      - A frame is a data link layer unit of data.

        帧是数据链路层的数据单元。

      - It contains the payload, source and destination MAC addresses, and error-checking information.

        它包含载荷、源和目的地MAC地址和错误检查信息。

15. Error control and flow control

    - **Error Control:**

      **错误控制：**

      - It manages the errors that occur during the transmission of frames.

        它管理在帧传输过程中发生的错误

      - Techniques like ARQ (Automatic Repeat reQuest) are used for error detection and correction.

        使用如ARQ（自动重复请求）这样的技术进行错误检测和校正

    - **Flow Control:**

      **流量控制**

      - It ensures the sender does not overwhelm the receiver by sending too many frames at once.

        它确保发送方不会通过一次发送太多帧来压垮接收方



16. Framing methods

* Byte count

  - How it works:

    - The frame starts with a field that contains the count of bytes in the frame.

      帧开始处有一个字段，包含帧中的字节计数。

    - The receiver uses this count to locate the end of the frame.

      接收者使用这个计数来定位帧的结束位置

  - Pros and Cons:

    - Simple but can be unreliable because if the count is erroneous or lost, it can be tough to locate the next frame.

      简单但可能不可靠，因为如果计数错误或丢失，定位下一帧会变得困难

* Flag bytes with byte stuffing

  - How it works:

    - A special flag byte sequence marks the beginning and end of a frame.

      一个特殊的标志字节序列标记帧的开始和结束

    - If this flag byte sequence appears in the data, it is “stuffed” with an escape byte to differentiate it from the actual flag bytes.

      如果数据中出现这个标志字节序列，它会被“填充”一个转义字节以区别于实际的标志字节

    - The receiver “destuffs” the data, removing the escape bytes and interpreting the flag bytes correctly to delineate the frames.

      接收者对数据进行“去填充”，移除转义字节，并正确解释标志字节来划定帧的边界

  - Pros and Cons:

    - More reliable than byte count but introduces overhead due to stuffing.

      比字节计数法更可靠，但由于填充而导致开销

* Flag bits with bit stuffing

  - How it works:

    - Similar to byte stuffing but operates on bits.

      类似于字节填充法，但操作在位上

    - A special bit pattern marks the beginning and end of the frame.

      一个特殊的位模式标记帧的开始和结束

    - If this pattern appears in the data, a '0' bit is stuffed after the five consecutive '1' bits to avoid confusion.

      如果这个模式出现在数据中，五个连续的‘1’位之后会被填充一个‘0’位，以避免混淆

    - The receiver destuffs the bits, removing any stuffed bits and interpreting the flag bits correctly to delineate the frames.

      接收者去除任何填充位，并正确解释标志位以划定帧的边界

  - Pros and Cons:

    - More flexible compared to byte stuffing as it operates on the bit level, but also introduces overhead due to stuffing.

      与字节填充相比，由于它在位级上操作，更为灵活，但也由于填充而引入了开销

* Physical layer coding violations

  - How it works:

    - This method uses violations of the encoding scheme used at the physical layer to mark the beginning and end of frames.

      该方法使用物理层编码方案中的违规来标记帧的开始和结束

    - For example, in a scheme where voltage levels represent bits, an illegal voltage level not used for either 0 or 1 may be used to indicate frame boundaries.

      例如，在一个电压水平代表位的方案中，一个非法的电压水平（既不用于0也不用于1）可能被用来表示帧边界

  - Pros and Cons:

    - Highly reliable in detecting frame boundaries but requires a more sophisticated physical layer.

      在检测帧边界方面非常可靠，但需要更精密的物理层。



17. Utopia: No Flow Control or Error Correction

* When should we use Utopia?

  Utopia refers to an ideal condition where there is no need for flow control or error correction due to the absence of errors or data loss. It would be used in highly reliable and low-latency networks, but it’s more theoretical than practical, as real-world networks typically require both error control and flow control.

  乌托邦指的是由于缺乏错误或数据丢失而无需流控制或错误校正的理想状态。它会用于高可靠性和低延迟的网络，但它更多的是理论上的，因为现实世界的网络通常需要错误控制和流量控制。



18. Adding Flow Control: Stop-and-Wait

* How it works?

  In the Stop-and-Wait protocol, the sender sends one frame and then waits for an acknowledgment from the receiver before sending the next frame.

  在停-等协议中，发送方发送一个帧，然后等待接收方的确认，然后再发送下一个帧。



19. Adding Error Correction: Sequence Numbers and ARQ

* Why we use sequence number?

  Sequence numbers are used to identify the order of the frames sent, so the receiver can properly reorder them, and detect any missing frames. ARQ is a protocol for automatically repeating frames when errors are detected.

  序列号用于标识发送的帧的顺序，以便接收方可以正确地重新排序它们，并检测任何缺失的帧。ARQ是一种在检测到错误时自动重复帧的协议。



20. How bidirectional transmission works?

    Bidirectional transmission allows data to be sent in both directions, either simultaneously (full-duplex) or alternately (half-duplex).

    双向传输允许数据在两个方向上发送，要么同时（全双工），要么交替（半双工）。



21. What is piggybacking?

    Piggybacking is a technique where the acknowledgment of a received frame and a data frame are sent together to utilize the bandwidth efficiently.

    搭载是一种技术，在这种技术中，接收到的帧的确认和数据帧一起发送，以有效利用带宽。





22. Three bidirectional sliding window protocols

* One-bit sliding window

  等同于停-等

  - What is it:

    - This is the simplest sliding window protocol. The window size is one, meaning that the sender can send only one frame at a time and must then wait for an acknowledgment from the receiver before sending the next frame.

      这是最简单的滑动窗口协议。窗口大小为一，这意味着发送者一次只能发送一个帧，然后必须等待接收者的确认后才能发送下一个帧。

  - How it works:

    - The sender sends a frame and starts a timer, waiting for an acknowledgment.

      发送者发送一个帧并开始计时，等待确认。

    - If the acknowledgment is received before the timer expires, the sender sends the next frame; if not, the sender resends the frame.

      如果在计时器到期前收到确认，则发送者发送下一个帧；如果没有，发送者重新发送该帧

    - This approach is simple but can be inefficient, especially over high-latency links.

      这种方法简单，但在高延迟链路上可能会效率低下

* go-back-n

  - What is it:

    - In this protocol, the sender can send multiple frames before needing an acknowledgment, but it uses a fixed-size window to limit the number of unacknowledged frames.

      在此协议中，发送者在需要确认前可以发送多个帧，但它使用固定大小的窗口来限制未确认帧的数量

  - How it works:

    - The sender maintains a window of frames that can be sent without receiving acknowledgments.

      发送者维持一个可以在收到确认前发送的帧的窗口

    - If a frame is lost or an error occurs, the sender goes back and resends all frames starting from the lost or erroneous frame.

      如果一个帧丢失或出现错误，发送者会返回并从丢失或错误的帧开始重新发送所有帧

    - The receiver only sends acknowledgment for the last correctly received in-order frame and ignores out-of-order frames.

      接收者只为最后正确接收的有序帧发送确认，并忽略乱序帧

    - This is more efficient compared to one-bit sliding window but can still have high overhead if the error rate is high.

      与一位滑动窗口相比，这更加高效，但如果错误率高，仍然可能有很高的开销

  发送方可以在需要确认之前发送多个帧，但如果检测到错误，将重新传输窗口中的所有帧

* selective repeat

  - What is it:

    - This protocol also allows the sender to send multiple frames before receiving acknowledgments, but it allows the receiver to accept frames out of order and buffer them.

      该协议还允许发送者在收到确认前发送多个帧，但它允许接收者接收乱序帧并缓存它们。

  - How it works:

    - The sender maintains a window of frames that can be sent, similar to Go-Back-N.

      与回退N类似，发送者维持一个可以发送的帧的窗口

    - The receiver sends individual acknowledgments for each correctly received frame, even if it's out of order.

      接收者为每个正确接收的帧发送单独的确认，即使它是乱序的

    - If a frame is lost or erroneous, only the specific frame needs to be resent, not all the subsequent frames.

      如果一个帧丢失或有错误，只需要重新发送特定的帧，而不是所有后续的帧

    - This approach is efficient in terms of bandwidth usage, especially in high-latency or high-error-rate environments, as it minimizes the number of retransmissions.

      在高延迟或高错误率的环境中，这种方法在带宽使用方面很高效，因为它将重传次数降到最低

  发送方可以发送多个帧，接收方可以选择性地确认它们，允许发送方仅重新传输未正确接收的帧