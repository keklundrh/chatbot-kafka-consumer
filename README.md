# chatbot-kafka-consumer
## Introduction
**Red Hat OpenShift Data Science**, a managed cloud platform for Data Scientists
and Developers of intelligent applications, supports the full Machine Learning
lifecycle by providing a robust, scalable platform and a flexible, interactive
environment for teams to do their work. **Starburst Galaxy**, based on open
source Trino (formerly PrestoSQL), is a managed service providing a single point
of access to your data without having to move it to a central repository.
**Starburst Galaxy** focuses on the first, and often most difficult problem
teams face when starting a new project - **The Acquisition and Preparation of
Data**.

**Figure:** Machine Learning Lifecycle

![MLLC](support/ml-lifecycle-desktop.svg)

**Figure:** High level view of Starburst's Data Consumption Layer
![Consumption view](support/higher-level-arch.png)

## Demonstration
This demonstration will illustrate how quickly a Data Scientist can join
streaming data from a **Customer Support Chatbot** to both the **Customer** and
**Financial** data domains in relational databases. This process is
straightforward thanks to **Starburst Data's** data consumption layer
abstractions. 

## High Level Architecture 
![Data source view](support/high-level-arch.png)

## Requirements
Please see [chatbot-env-setup](https://github.com/keklundrh/chatbot-env-setup)
for instructions to create a comparable demo environment. 

You will need:
- [Red Hat OpenShift Data
  Science](https://www.redhat.com/en/technologies/cloud-computing/openshift/openshift-data-science)
- [A Kafka
  queue](https://www.redhat.com/en/technologies/cloud-computing/openshift/openshift-streams-for-apache-kafka) with a 'messages' topic.
- PostgreSQL with staged data (Customer domain)
- PostgreSQL with staged data (Finance domain)
- Hive metastore 
- Jupyter notebooks (this repo)  

## Getting Started
You will need an environment setup before getting started (see requirements
section). 

Log into your Red Hat OpenShift Data Science environment and select an
appropriate notebook image. Be sure to include the following environment
variables (unique to your environment):
- `KAFKA_BOOTSTRAP_SERVER`
- `KAFKA_SECURITY_PROTOCOL`
- `KAFKA_SASL_MECHANISM`
- `KAFKA_USERNAME`
- `KAFKA_PASSWORD`
- `TRINO_USERNAME`
- `TRINO_HOSTNAME`
- `TRINO_PORT`

Here's a quick highlight of the notebooks:
- `0_kafka_prepopulate.ipynb`:  connect to kafka and prepopulate the queue with
  randomized customer numbers and support requests.
- `1_kafka_producer.ipynb`: simple "chatbot" to illustrate sending single
  messages 
- `2_kafka_consumer.ipynb`: simple consumer listening for our hello world
  exercise in the previous notebook
- `3_trino_explore.ipynb`: connect to Starburst, pull and explore your data.
- `4_build_features.ipynb`: build features for use in future models.
- `5_nltk.ipynb`: exercise for the reader.
