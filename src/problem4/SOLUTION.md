## Error Screenshot

![Error Screenshot](Error%20Occurred.PNG)


## Problems Identified


- **Services may start before dependencies are ready**  
  The `api` service may start before `postgres` or `redis` are fully initialized, which can cause connection failures and make the API unreliable during startup.

- **Redis memory configuration warning**  
  Redis logs indicate that memory overcommit is not enabled on the host system. Without this setting, Redis background operations may fail under certain conditions.

- **No health checks for monitoring**  
  The services do not define health checks. Without health checks, Docker cannot determine whether containers are actually functioning correctly, which makes automated recovery and monitoring more difficult.

## How I Diagnosed the Issues

- Reviewed the `docker-compose.yml` file to understand the service configuration, dependencies, and environment variables.


## Fixes Applied

- **Improved service dependency configuration**  
  Updated service dependencies so that the API waits for PostgreSQL to become healthy before starting, improving startup reliability.

- **Documented Redis host configuration requirement**  
  Noted the Redis memory overcommit warning and documented the required host configuration (`vm.overcommit_memory=1`) to prevent potential Redis background operation failures.

- **Added health checks to PostgreSQL**  
  Implemented a health check using `pg_isready` so that dependent services can verify when the database is ready to accept connections.



## Production Improvements

- **Add monitoring (Prometheus + Grafana)**  
  Implement monitoring to collect metrics from the services and visualize system performance and health. This helps detect issues early and provides better operational visibility.

- **Add readiness and liveness checks**  
  Implement readiness and liveness probes so that orchestration platforms or monitoring systems can detect unhealthy services and take corrective actions automatically.

