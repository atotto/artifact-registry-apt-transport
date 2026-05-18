This repository contains plugin for the APT package tool which adds support for accessing authenticated Artifact Registry repositories.

## Authentication

The following authentication methods are supported, checked in this order:

1. **`CLOUDSDK_AUTH_ACCESS_TOKEN` environment variable** (highest priority)
   Set this to a valid GCP access token. You can obtain one with:
   ```sh
   export CLOUDSDK_AUTH_ACCESS_TOKEN=$(gcloud auth print-access-token)
   ```
   Note that tokens are valid for 1 hour.

2. **`Acquire::gar::Service-Account-JSON`** apt config option
   Path to a service account JSON key file.

3. **`Acquire::gar::Service-Account-Email`** apt config option
   Service account email for GCE instance metadata-based authentication.

4. **Application Default Credentials (ADC)**
   Uses `gcloud auth application-default login` credentials automatically.
