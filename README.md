# homelab-toolkit
A curated collection of Bash scripts for managing and maintaining Linux home servers.

# 📦 dcu (Docker Compose Utility)

`dcu` is a powerful and user-friendly Bash script designed to simplify the management of Docker Compose services. It provides a comprehensive set of features for starting, stopping, monitoring, and updating services, all with a focus on efficiency and ease of use.

## Features

- Start or stop all Docker Compose services with a single command
- Manage individual services with targeted commands
- Display detailed status of running containers and services
- Check for available updates for services, with interactive selection for applying updates
- Apply updates to all services or specific services
- Parallel processing for faster operations
- Enhanced logging with color-coded output

## Setup

1. Clone this repository:

   ```bash
   git clone https://github.com/meminens/homelab-toolkit.git
   cd homelab-toolkit
   ```

2. Make the script executable:

   ```bash
   chmod +x docker/dcu
   ```

3. Add the script to your PATH:

   ```bash
   export PATH="$PATH:$HOME/homelab-toolkit/docker"
   ```

   To make this change permanent, add the above line to your shell configuration file (e.g., `~/.bashrc` or `~/.zshrc`).

## Usage

Run `dcu` with one of the following commands:
```bash
dcu start               # Start all Docker Compose services
dcu stop                # Stop all Docker Compose services
dcu status              # Display status of all services
dcu st <service>        # Start a specific service
dcu sp <service>        # Stop a specific service
dcu rs <service>        # Restart a specific service
dcu update              # Check for updates and interactively apply them
```

## Configuration

- **Base Directory**: By default, `dcu` looks for Docker Compose projects in `$HOME/Docker/Hub`. You can override this by setting the `DCU_BASE_DIR` environment variable.
- **Parallel Jobs**: The maximum number of parallel jobs for processing services is set to 16 by default. This can be adjusted by modifying the `MAX_PARALLEL_JOBS` variable in the script.

## Examples

- Start all services:

  ```bash
  dcu start
  ```

- Check for updates and selectively apply them to desired services:

  ```bash
  dcu update
  ```

- Stop a specific service:

  ```bash
  dcu sp Immich
  ```

- Use a custom base directory:

  ```bash
  DCU_BASE_DIR=/custom/path dcu status
  ```

## Notes

- Ensure that `jq` and `regctl` are installed for update checking functionality. You can install them using your package manager (e.g., `sudo apt install jq` or `sudo pacman -S regctl`).
- The script supports multiple Docker Compose file naming conventions, including `docker-compose.yml`, `docker-compose.yaml`, `compose.yml`, and `compose.yaml`.

For more information, run:

```bash
dcu help
```
