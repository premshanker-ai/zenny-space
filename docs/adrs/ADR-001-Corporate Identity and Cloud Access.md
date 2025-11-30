# ADR-001: Corporate Identity and Cloud Access

* **Status:** Accepted
* **Date:** 2025-11-29
* **Context:**
    We are building "Zenny Space." To apply for the Google for Startups scholarship and manage our cloud resources securely, we cannot use personal Gmail accounts (`@gmail.com`). We need a professional identity.

* **Decision:**
    We have established a **Google Cloud Organization** by:
    1.  Purchasing the domain `zennyspace.com`.
    2.  Registering for Google Workspace (Cloud Identity).
    3.  Verifying domain ownership via DNS TXT records.

* **Consequences:**
    * **Professionalism:** We now have a legitimate business identity for scholarship applications.
    * **Security:** We have a "Root Node" for our cloud. This means we can manage permissions centrally. If a founder leaves, we can revoke access instantly.
    * **Cost:** We are using the "Cloud Identity Free" tier to minimize startup costs while retaining enterprise security features.