# ADR-001: Foundation Tech Stack and Identity Management

* **Status:** Accepted
* **Date:** 2025-11-29
* **Context:**
    Zenny Space requires a mental health platform capable of handling sensitive user data while providing real-time AI interactions. We have two competing constraints:
    1.  **Startup Velocity:** We need to ship an MVP immediately.
    2.  **Enterprise Governance:** We must adhere to strict IAM (Identity) and Security standards to prepare for future compliance (SOC2/HIPAA).

* **Decision:**
    We will implement a **Polyglot Microservices Architecture** on **Google Cloud Platform (GCP)**.

    **1. Compute Strategy: Serverless (Cloud Run)**
    * We will use Cloud Run to host containerized services.
    * *Justification:* Eliminates cluster management overhead (k8s) while allowing scale-to-zero to minimize costs during the pre-revenue phase.

    **2. Identity Management: Cloud Identity & Organization Node**
    * We will bootstrap a GCP Organization Node using Cloud Identity.
    * *Justification:* Enables centralized policy enforcement (Organization Policies) distinct from consumer Gmail accounts.

    **3. Polyglot Backend**
    * **Core Business Logic:** Ruby on Rails. (Chosen for rapid REST API development and ActiveRecord maturity).
    * **AI/ML Layer:** Python. (Chosen for native client libraries for Vertex AI and data processing capabilities).
    * *Integration:* Services will communicate via Pub/Sub or gRPC, not direct database sharing.

* **Consequences:**
    * **Positive:** Separation of concerns. The AI logic does not clutter the transactional Rails codebase.
    * **Negative:** Adds complexity to the CI/CD pipeline, as we must build and deploy two distinct containers.
    * **Mitigation:** We will use Google Cloud Build with parallel steps to handle multi-service deployments.