# Open Notebook Caddy Proxy

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/deploy/open-notebook?referralCode=ZqgrJ0)

Caddy edge proxy used by the [Open Notebook Railway template](https://railway.com/deploy/open-notebook). It presents one public origin while routing the web interface and API to their private Railway services.

## Configuration

The container reads these environment variables:

- `PORT`
- `WEB_ENDPOINT`
- `API_ENDPOINT`

The image is pinned to Caddy 2.11.4. This repository is a component of the complete template rather than a standalone Open Notebook deployment.
