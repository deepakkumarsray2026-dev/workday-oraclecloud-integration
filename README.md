# Workday-OracleCloud-Integration

# Workday Studio Integration with Oracle Cloud Object Storage

## Overview

This project demonstrates a custom integration framework built in **Workday Studio** to enable connectivity between **Workday Prism Analytics** and **Oracle Cloud Infrastructure (OCI) Object Storage**.

Workday Prism provides delivered connectivity for several cloud storage platforms such as:

* AWS S3
* Microsoft Azure Storage
* Google Cloud Storage / BigQuery
* Snowflake

However, native support for **Oracle Cloud Object Storage** is currently unavailable.

This project addresses that gap by implementing OCI-compatible REST authentication and request signing directly within Workday Studio using custom Java components.

---

## Problem Statement

Oracle Cloud Object Storage APIs require requests to be authenticated using:

* RSA SHA256 request signing
* Canonical request generation
* OCI-specific authorization headers
* Signed REST requests

Unlike standard OAuth or bearer-token APIs, OCI APIs require cryptographic request signing for every request.

Workday Studio does not provide built-in support for OCI request signing, making direct integration challenging.

---

## Solution

This integration extends Workday Studio capabilities by introducing custom Java-based request signing and authenticated REST communication with Oracle Cloud Object Storage.

### Key Features

* OCI REST API integration from Workday Studio
* RSA SHA256 request signing
* Dynamic Authorization header generation
* Secure private key handling
* File retrieval from OCI Object Storage
* Reusable signing utility components
* Error handling and logging framework

---

## Architecture

```text
Workday Studio
       |
       |  REST API Request
       |  + RSA SHA256 Signature
       v
Oracle Cloud Object Storage
       |
       v
File Retrieval / Processing
```

---

## Technical Components

### Workday Studio Components

* HTTP Send
* Mediation Components
* Properties / Variables

### Custom Java Utilities

The Java layer is responsible for:

* Building canonical signing strings
* RSA SHA256 signing
* Header generation
* Date formatting
* Request authentication

---

## OCI Request Signing Flow

The integration follows Oracle Cloud Infrastructure signing standards:

1. Construct canonical request string
2. Generate SHA256 RSA signature
3. Encode signature using Base64
4. Build Authorization header
5. Execute authenticated REST request

---

## Security Considerations

This implementation was designed with security best practices in mind:

* No hardcoded credentials
* Secure private key storage
* Reusable signing utilities
* Separation of configuration and logic
* Secure HTTPS communication

---

## Use Cases

This integration can be used for:

* Workday Prism data ingestion
* OCI-hosted inbound files
* Enterprise cloud integration
* Automated file retrieval workflows

---

## Technologies Used

* Workday Studio
* Java
* Oracle Cloud Infrastructure (OCI) REST APIs
* RSA SHA256 Cryptography
* RESTful Web Services

---

## Challenges Solved

One of the biggest challenges solved by this project was implementing OCI-compatible cryptographic request signing within Workday Studio, which does not natively support this authentication mechanism.

This required combining:

* Custom Java extensions
* OCI API security standards
* Studio orchestration logic
* Secure integration design

---

## Disclaimer

This project is intended for educational and enterprise integration demonstration purposes. Ensure your implementation complies with your organization's security and compliance standards before production deployment.

---

## Author

Developed as a custom Workday Studio integration solution to extend Workday Prism Analytics connectivity with Oracle Cloud Infrastructure Object Storage.
