# MindConnect – Social Media & Doctor Booking (Microservices Project)

⚠️ **Note:** This is a **microservices-based project**. Each microservice has its own repository. Links to the actual repos are provided below.

---

## Overview
MindConnect is a large-scale platform combining **social media** and **doctor booking** modules.  
The **Social Media Module** powers posts, feeds, and follow mechanics for **millions of users**, built with **high-throughput, low-latency microservices**.

---

## Microservices & Repositories
Each microservice is independent and deployed separately:

| Service       | Description                                         | GitHub Link |
|---------------|-----------------------------------------------------|-------------|
| **Post**      | Handles creation, updates, and storage of user posts | [Post Service](#) |
| **Feed**      | Generates user timelines efficiently using Kafka fan-out | [Feed Service](#) |
| **Follow**    | Manages follower/following relationships & notifications | [Follow Service](#) |

Each repo includes setup instructions and can be run independently.  

---

## Architecture & Key Highlights
- **Communication:** gRPC + REST for inter-service calls  
- **High-Scale Fan-Out:** Processed **5M followers** in ~7–9 minutes using Kafka (5 partitions, 6 consumers)  
- **Batching & Parallelism:** Batched **2,000 followers per partition** for efficient fan-out  
- **Rate Limiting:** MongoDB writes capped at **10K ops/sec** using **Guava Leaky Bucket**  
- **Resilience & Throughput:** Multi-threaded producers + parallel consumers handle peak traffic seamlessly  

---

## Architecture Diagrams
- **High-Level Architecture:** UserService, DoctorService, SocialMediaService, BookingService, API Gateway, databases/storage  
- **Social Media Microservices:** Post, Feed, and Follow services with Kafka fan-out, MongoDB schema, and batching logic  

*(Add your diagrams here if available, e.g., `screenshots/architecture.png`)*  

---

## Tech Stack
- **Backend:** Spring Boot  
- **Database:** MongoDB  
- **Messaging:** Kafka  
- **Communication:** gRPC + REST  
- **Utilities:** Guava Rate Limiter, Multi-threaded Processing  

---

## Design Notes
- Detailed **design decisions** and **system design thinking** documented here → [Design Notes](#)  
- Covers experimentation with **fan-out strategies**, **idempotent APIs**, and **resilient scaling**  

---

## Resume Highlights
- Architected a **distributed fan-out pipeline** to process posts from users with **up to 5M followers**.  
- Built **3 production-grade microservices** (Post, Feed, Follow) with gRPC + REST.  
- Optimized Kafka throughput (5 partitions, 6 consumers, batching of 2K) to achieve **~7–9 min fan-out completion**.  
- Implemented **idempotent POST APIs** and **MongoDB rate-limiting at 10K ops/sec**.  
