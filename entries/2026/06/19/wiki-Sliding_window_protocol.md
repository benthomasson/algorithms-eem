---
source: sources/wiki-Sliding_window_protocol.md
source_url: https://en.wikipedia.org/wiki/Sliding_window_protocol
---

## Sliding Window Protocol

The sliding window protocol is a flow-control and reliable-delivery mechanism used in packet-based data transmission. It allows a sender to transmit multiple packets before requiring acknowledgment, improving throughput over high-latency links. The "window" defines how many unacknowledged packets may be in flight simultaneously, and it slides forward as acknowledgments arrive. Sliding windows operate at the data link layer (OSI layer 2) and the transport layer (TCP), and are foundational to protocols like TCP, HDLC, UUCP-g, and ZMODEM.

## Key Concepts

- **Window**: The logical boundary of packets the transmitter may send before receiving acknowledgment. The window slides forward as ACKs arrive.
- **Sequence numbers**: Each packet (or byte, in TCP) gets a unique consecutive sequence number. The receiver uses these to reorder, detect duplicates, and identify missing data.
- **Fixed-size sequence numbers**: Sliding windows allow unlimited data transfer using finite (modular) sequence numbers, provided the modulus N satisfies N >= wt + wr.
- **Key variables**:
  - *nt*: next packet to transmit (first unsent)
  - *nr*: first packet not yet received (receiver side)
  - *ns*: one past the greatest sequence number received
  - *na*: greatest acknowledgment received by transmitter
  - Invariant: na <= nr <= ns <= nt <= na + wt
- **TCP window field**: 16-bit field in TCP header, maximum window = 64 KB (without scaling).
- **Slow start**: Transmitter begins with a low packet count, increases after each ACK until hitting the window threshold, then switches to one-packet-per-ACK.
- **Bandwidth-delay product (BDP)**: The window must be larger than the BDP to avoid underutilizing the link. If window < BDP, the protocol throttles effective bandwidth.
- **Congestion control**: Dynamic window sizing prevents network saturation; the application layer hands off congestion management to TCP's sliding window.

## Commands and Syntax

No CLI commands — this is a protocol-level concept. Key formulas:

- **Sequence number modulus constraint**: N >= wt + wr (general case). For Go-Back-N (wr=1): N > wt, so wt <= N-1.
- **Transmitter may send**: packet nt if nt < na + wt
- **Receiver accepts**: packet x if nr <= x < nr + wr
- **Stop-and-wait**: wt=1, wr=1, N=2 (1-bit sequence number)
- **Go-Back-N**: wt > 1, wr=1, N >= wt + 1
- **Selective Repeat**: wt > 1, wr > 1, N >= wt + wr
- **HDLC example**: 3-bit sequence number (N=8). Go-Back-N: wt <= 7. Selective Repeat with wr=2: wt <= 6.

## Relationships

- **Stop-and-Wait ARQ**: Simplest sliding window (wt=1, wr=1); a degenerate case, not a separate protocol.
- **Go-Back-N ARQ**: Sliding window with wr=1; receiver discards out-of-order packets, causing retransmission of entire window on loss.
- **Selective Repeat ARQ**: Most general form; receiver buffers out-of-order packets, only the lost packet is retransmitted.
- **TCP**: Uses sliding windows for both flow control (receiver window) and congestion control (congestion window). TCP window scaling (RFC 1323) extends beyond 64 KB.
- **Bandwidth-Delay Product**: Determines minimum window size for full link utilization.
- **Automatic Repeat Request (ARQ)**: Sliding window is an optimization over basic ARQ's stop-and-wait behavior.
- **Congestion control algorithms** (slow start, congestion avoidance): Govern how the window size changes dynamically.
- **HDLC**: Data link protocol using 3-bit sequence numbers; supports both Go-Back-N and selective repeat variants.
- **Serial number arithmetic**: Governs how modular sequence number comparisons work.

## Exam-Relevant Points

- The sequence number space must satisfy **N >= wt + wr** to avoid ambiguity. This is the most commonly tested constraint.
- **Stop-and-wait** needs only N=2 (1 bit). **Go-Back-N** with N=8 allows wt <= 7. **Selective Repeat** with N=8 and wr=2 requires wt <= 6.
- Go-Back-N is inefficient on lossy links because all packets after a loss must be retransmitted; Selective Repeat only retransmits the lost packet.
- TCP's receiver window field is **16 bits**, limiting the base window to **64 KB** (extendable via RFC 1323 window scaling).
- The window must exceed the **bandwidth-delay product** to fully utilize the link; otherwise the sender idles waiting for ACKs.
- **Slow start** doubles the window each RTT (exponential growth) until reaching the threshold, then grows linearly (congestion avoidance).
- In the ambiguity examples, the core issue is always: can the receiver distinguish a **new packet** from a **retransmission** given only the modular sequence number? The N >= wt + wr rule prevents this ambiguity.
- Acknowledgments carry *nr* (cumulative ACK of all packets below that number), not individual packet numbers — though selective ACK (SACK) extends this.
