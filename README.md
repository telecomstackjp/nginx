# nginx
Web Hosting Server
# My Coolify Nginx Project

This project demonstrates a simple setup using Docker Compose, Nginx, and Coolify. It serves static content from an Nginx container that is configured and deployed using Coolify.

## Prerequisites

*   Docker:  Install Docker on your machine.  See [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
*   Docker Compose:  Install Docker Compose.  It is usually included with Docker Desktop or can be installed separately. See [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
*   Coolify:  You need a working Coolify instance to manage the deployment.

## Getting Started

1.  **Clone this repository:**

    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

    Replace `<repository-url>` with the URL of your GitHub repository and `<repository-directory>` with the name of the cloned directory.

2.  **Configure Coolify:**

    *   In your Coolify instance, set up a new project.
    *   Configure a new source to point to your GitHub repository.
    *   Create a new application in Coolify using the Docker Compose configuration.
    *   Ensure that the Coolify network is set to `coolify-network`.

3.  **Run Docker Compose (Optional - for local testing):**

    You can use docker-compose to run the Nginx container locally for testing purposes.

    ```bash
    docker-compose up -d
    ```

    This will start the Nginx container in the background.  You can access the website at `http://localhost`.

4.  **Deploy with Coolify:**

    Once you have configured Coolify, deploy the application. Coolify will handle the build, deployment, and management of your Nginx container.

## Configuration

*   **`docker-compose.yaml`:** Defines the Nginx service, volume mappings, and network configuration.  Crucially, the network is set to `coolify-network` so Coolify can manage it.
*   **`nginx/nginx.conf`:**  Configures the Nginx web server.  It's set up to serve static files from the `/usr/share/nginx/html` directory.  It listens on port 80, assuming Coolify will handle HTTPS termination.
*   **`nginx/html/`:** Contains the website's static files.

## Notes

*   This setup assumes Coolify is handling SSL (HTTPS) termination. If you want to manage SSL certificates directly in Nginx, you'll need to modify the `nginx.conf` file and the `docker-compose.yaml` to include certificate files and listen on port 443.  **This is not recommended if you're using Coolify as intended.**
*   You can customize the `nginx.conf` file to configure Nginx according to your specific needs (e.g., setting up reverse proxies, configuring caching, enabling Gzip compression).
*   The `healthcheck` in the `docker-compose.yaml` helps ensure that the Nginx container is running correctly.  Coolify will also use this health check.

## Contributing

Feel free to contribute to this project by submitting pull requests.

## License

[Telecom Stack - Free Licence]
