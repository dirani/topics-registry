📘 topics-registry — Repository Description
topics-registry is the source‑of‑truth repository for all Kafka‑related artifacts used across the platform. It contains the raw, human‑authored definitions of:

-	Kafka topics
-	Kafka replicators
-	Kafka transformers

These artifacts are stored in simple, standalone Helm template fragments under a clean folder structure:
```
topics/
replicators/
transformers/
```
This repository is intentionally lightweight and focused on authoring, reviewing, and validating Kafka infrastructure definitions before they are consumed by the platform.

🔍 Purpose
The goal of topics-registry is to centralize and standardize the definition of Kafka resources, ensuring:

-	consistent naming and configuration
-	early validation through automated linting
-	clear ownership and review workflows
-	separation between authoring (this repo) and deployment (topic-controller)
All changes to Kafka artifacts originate here.

🧪 CI & Validation
Every pull request triggers automated Helm linting to ensure that:
-	YAML is valid
-	Helm templates render correctly
-	no malformed definitions reach the main branch
This shifts quality control to the earliest possible stage.

🔄 Sync to topic-controller
When changes are merged into main, a sync workflow automatically:
-	clones the topic-controller repository
-	copies the validated Kafka artifacts into the appropriate folders
-	opens a pull request or pushes updates (depending on configuration)
This ensures that the controller always receives clean, validated definitions without manual copying or risk of human error.

🧭 Role in the Platform
topics-registry is the authoritative catalog of Kafka infrastructure. It is designed to be:
-	simple to contribute to
-	easy to review
-	safe to automate
-	compatible with future evolution (e.g., metadata, CRDs, ext‑hub integration)
It acts as the upstream source for all Kafka‑related deployments in the platform
