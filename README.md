# ct-patching-scanning

# Cornell University Cloud Team Patching and Scanning Automation

Scripts and templates relevant to patching and scanning EC2 instances

See https://confluence.cornell.edu/display/CLOUD/Beta+AWS+Inspector+and+Patching

## Change Log

### 2024-11-07
- Moved and renamed repo to https://github.com/cu-cit-cloud-team/aws-patching-scanning; was https://github.com/CU-CommunityApps/ct-patching-scanning.
- Removed unused Lambda function and AMI data file.
- Renamed default branch to `main`; was `master`.
- Added bucket policy to S3 bucket and set public access block for bucket.

## Table of Contents

* [cloudformation](cloudformation) contains CloudFormation templates for deploying this functionality.

* [scripts](scripts) contains reporting scripts used by Jenkins jobs

## Patch Baseline Testing

The patch baselines in [cloudformation/15-patch-baselines.yaml](cloudformation/15-patch-baselines.yaml) are based on the AWS default patch baselines, but slightly modified to patch additional packages that Inspector would otherwise trigger on.

## Docker

This repo comes with `Dockerfile` and `docker-compose.yml` files that can help provide an execution environment for running the scripts in `scripts/`.

### Prerequisites

`docker` and `docker-compose` must be installed and configured. See https://docs.docker.com/install/.

### Recommended Usage (docker-compose)

Bring container up (it will build if there isn't one locally already):

```bash
docker-compose up --detach
```

Attach to bash shell in container to run scripts:

```bash
docker-compose exec awspython bash
```

Stop Docker container and clean up after `docker-compose`:

```bash
docker-compose down
```