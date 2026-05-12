# Concurrency-Control-and-Data-Consistency-in-Distributed-Web-Apps
A research paper on concurrency and data consistency on modern web apps
Author: Mac Rolins Odera Date: April 2026  
📄 Overview
This repository contains the seminar paper investigating the mechanisms of concurrency control and the spectrum of data consistency models in modern distributed systems. As web architectures transition from monoliths to globally distributed networks, maintaining data integrity without compromising performance or availability has become a fundamental engineering challenge.  This research evaluates the shift from rigid ACID constraints to basically available (BASE) models, analyzing the theoretical limits, algorithmic protocols, and architectural trade-offs required to build resilient, high-performance web applications. 
🎯 Key Research Areas
1. Theoretical Foundations
   ACID vs. BASE: Explores the duality between the traditional ACID model (prioritizing transaction integrity and isolation) and the modern BASE model (prioritizing eventual consistency and high availability for global-scale infrastructure).
   
    CAP and PACELC Theorems: Analyzes the fundamental laws of distributed trade-offs. It emphasizes the PACELC theorem, which posits that even in a healthy network without partitions, systems must inherently choose between latency and consistency.

  2. Concurrency Control ProtocolsSystematic comparison of the algorithms that govern simultaneous access to shared records:
         Two-Phase Locking (2PL): A pessimistic approach ensuring serializability but introducing lock contention and deadlock risks in distributed contexts.
         Optimistic Concurrency Control (OCC): Assumes conflicts are rare and validates at commit time, which is fast but wastes resources in high-contention environments.
         Multi-Version Concurrency Control (MVCC): The industry standard over the last decade. By maintaining multiple physical versions of a logical object, it ensures writers do not block readers and vice versa.

 3. Real-World Architectural Case Studies
       Google Spanner (CP System): A globally distributed SQL database achieving linearizability through "TrueTime"—a synchronized global clock service utilizing GPS and atomic clocks.
       Amazon Dynamo (PA/EL System): Prioritizes high availability and write operations (e.g., shopping carts) by utilizing sloppy quorums, hinted handoffs, and vector clocks for eventual consistency and causal history tracking.

 4. Distributed State Management PatternsExamines modern coordination strategies for microservices and serverless environments:
       The Saga Pattern: Manages long-running processes across services via a sequence of local transactions and compensating transactions (rollbacks) upon failure.
         The Transactional Outbox Pattern: Solves the "dual-write problem" by writing state updates and message payloads into the same database via a single local transaction, ensuring consistent event publishing.

5. Emerging Trends (2025-2026)
   Edge Computing & Causal Consistency: Leveraging the Actor model to enforce causal consistency—the strongest viable consistency level for fault-tolerant, low-latency edge operations.
   Serverless 2.0: Moving beyond stateless functions to "Durable" workflows capable of tracking long-running user sessions and state persistence.
   Hardware-Aware Protocols: Utilizing Remote Direct Memory Access (RDMA) to bypass CPU/OS stacks, drastically reducing network latency and improving throughput for high-contention data.

    💡 Conclusion & RecommendationsThe paper concludes that there is no universal consistency model. Architects must adopt a "Consistency by Design" approach: strictly applying strongly replicated models to financial or identity data, while leveraging eventually or causally consistent models for user interactions.  
