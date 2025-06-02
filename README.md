# Kafka-Kraft
Helm Chart Kafka with Kraft mode.

I've created a complete Helm project for Kafka with Kraft mode (without ZooKeeper). Here is the structure of the project:

``sh
kafka/
├── Chart.yaml # Chart metadata
├── values.yaml # Default values
├── templates/ # Kubernetes templates
│ ├── _helpers.tpl # Help functions
│ ├── NOTES.txt # Post-installation instructions
│ ├── serviceaccount.yaml # ServiceAccount
│ ├── headless-service.yaml # Service headless
│ └── statefulset.yaml # StatefulSet
└── charts/ # Dependencies (empty for now)
```

Here is a summary of the files created:
1. Chart.yaml: Contains the chart's metadata, such as name, description, version, etc.

2. values.yaml: Contains all the configurable values for the Kafka deployment, organised into sections:
    - Replica configuration
    - Image configuration
    - Services configuration
    - Persistence configuration
    - Resource configuration
    - Security configuration
    - Kafka configuration

3. templates/helpers.tpl: Contains help functions for generating consistent names and labels.

4. templates/serviceaccount.yaml: Template for the ServiceAccount.

5. templates/headless-service.yaml : Template for the Service headless.

6. templates/statefulset.yaml : Template for the StatefulSet, which is the main component.

7. templates/NOTES.txt: Post-installation instructions for the user.

The main features of this Helm chart are :

- Deployment of Kafka in KRaft mode (without ZooKeeper)
- Configuration for 2 replicas
- Use of Confluent Kafka 7.5.0
- Configuring persistence with Longhorn
- Configuring security with security contexts
- Configuring resources (CPU, memory)
- Configuring services (headless and client)

To use this chart, you can run :

```sh
# To check template rendering
helm template kafka ./kafka -n kafka

# To install the chart
helm install kafka ./kafka -n kafka

# To update the chart
helm upgrade kafka ./kafka -n kafka
```