# Huawei Cloud Log Analytics Pipeline

## Overview

This project implements a log analysis pipeline on Huawei Cloud. It ingests logs using LTS, stores them in OBS, processes anomalies using MRS/Spark, and visualizes alerts using Grafana.

## Architecture

The architecture consists of the following components:

*   **Log Sources:** Applications, servers, and other systems generating logs.
*   **LTS (Log Tank Service):** Huawei Cloud's log collection and aggregation service. Used for efficient log ingestion.
*   **OBS (Object Storage Service):** Huawei Cloud's object storage service. Used for storing raw log data.
*   **MRS (MapReduce Service/Spark):** Huawei Cloud's big data processing service. Used for anomaly detection and aggregation.
*   **Alerting System:**  A system to trigger alerts based on detected anomalies (e.g., sending emails or notifications).
*   **Grafana Dashboard:** A visualization tool for monitoring alerts and log data.

## Components

*   **Grafana:** Used for data visualization.

## FinOps Cost Estimation

Estimating the exact cost is difficult without specific usage details, but here's a breakdown of potential costs:

*   **LTS:** Pricing is based on the volume of logs ingested and retained.  Consider configuring retention policies to manage costs.
*   **OBS:** Pricing is based on storage capacity and data transfer. Use lifecycle policies to archive older data to lower-cost tiers if applicable.
*   **MRS/Spark:** Pricing is based on the number of vCPUs and memory used. Optimize Spark jobs for efficiency and consider using spot instances for non-critical workloads to reduce costs. Shut down MRS clusters when not in use.
*   **Grafana:**  The Grafana instance (if deployed on an ECS instance) will incur costs based on the instance type. A small instance is sufficient for basic visualization.

To get a more accurate estimate, use the Huawei Cloud Pricing Calculator with realistic estimates for your log volume, storage requirements, and processing needs.

**Example Cost Scenarios:**

*   **Small Scale:**  Low log volume (GBs per day), minimal processing.  Estimated monthly cost: $50 - $200
*   **Medium Scale:** Moderate log volume (10s of GBs per day), regular anomaly detection. Estimated monthly cost: $200 - $1000
*   **Large Scale:** High log volume (100s of GBs or TBs per day), complex analytics. Estimated monthly cost: $1000+

**Cost Optimization Tips:**

*   **Retention Policies:**  Set appropriate retention policies in LTS and OBS to avoid storing unnecessary data.
*   **Data Compression:**  Compress log data before storing it in OBS.
*   **Spark Optimization:**  Optimize Spark jobs for performance to reduce processing time.
*   **Resource Scaling:**  Scale MRS clusters up or down based on demand.
*   **Spot Instances:**  Use spot instances for non-critical MRS workloads.
*   **Logging Level:** Adjust logging levels in your applications to reduce the volume of logs generated.

## Usage

1.  Deploy the docker-compose.yml file using Docker Compose.
2.  Configure LTS to collect logs from your applications and servers.
3.  Configure MRS/Spark to process logs and detect anomalies.
4.  Set up alerts based on detected anomalies.
5.  Create dashboards in Grafana to visualize alerts and log data.

