# Docker GitHub Actions Runner

This project provides customized GitHub Actions self-hosted runner Docker images with Docker-in-Docker (DinD) support, Go (Golang), and Node.js pre-installed. It is built upon the [`myoung34/github-runner`](https://github.com/myoung34/docker-github-actions-runner) base image.

## Features

- **Lightweight & Powerful**: Optimized Docker images for various Linux distributions.
- **Go Support**: Go (Golang) v1.25.9 pre-installed and configured.
- **Node.js Support**: Node.js v24 (with npm, npx, and corepack) pre-installed and configured.
- **Build Essentials**: Includes essential build tools like `gcc`, `g++`, `make`, and `pkg-config`.
- **Multi-Distro Support**: Available variants based on Ubuntu (Focal, Jammy, Noble) and Debian (Buster, Bookworm, Sid).
- **Automated Publishing**: Automatically updated and pushed to GHCR (GitHub Container Registry) via GitHub Actions.

## Supported Variants

The following tags are available on GHCR:

| Tag | Base OS |
| :--- | :--- |
| `latest` | Latest stable release |
| `bookworm` | Debian 12 (Bookworm) |
| `buster` | Debian 10 (Buster) |
| `focal` | Ubuntu 20.04 (Focal) |
| `jammy` | Ubuntu 22.04 (Jammy) |
| `noble` | Ubuntu 24.04 (Noble) |
| `sid` | Debian Unstable (Sid) |

## Usage

To run the runner using Docker, you can use the following command:

```bash
docker run -d --restart always \
  --name github-runner \
  -e REPO_URL="https://github.com/YOUR_USERNAME/YOUR_REPO" \
  -e RUNNER_NAME="my-runner" \
  -e RUNNER_TOKEN="YOUR_GITHUB_RUNNER_TOKEN" \
  -v /var/run/docker.sock:/var/run/docker.sock \
  ghcr.io/mehyaa/github-runner:latest
```

### Important Environment Variables

- `REPO_URL`: The URL of your GitHub repository (e.g., `https://github.com/user/repo`).
- `RUNNER_TOKEN`: The registration token obtained from GitHub.
- `RUNNER_NAME`: A unique name for your runner.
- `RUNNER_WORK_DIRECTORY`: The working directory for the runner (Optional).

## Docker-in-Docker (DinD)

These images require the host's `/var/run/docker.sock` to be mounted to allow running Docker commands (build, push, etc.) within your workflows.

## License

This project is licensed under the [MIT License](LICENSE).
