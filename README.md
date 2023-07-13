# API Gateway

This project serves as an API Gateway for managing and routing requests to various microservices. It is configured to work with a Eureka Server for service discovery and registration.

## Description

The API Gateway acts as a single entry point for clients to access multiple microservices. It provides centralized routing, load balancing, security, and other cross-cutting concerns.

## Prerequisites

Before running this project, ensure that you have the following prerequisites installed:

- Java Development Kit (JDK) 8 or above
- Maven

## Getting Started

To get started with the project, follow these steps:

1. Clone the repository to your local machine:

   ```
   git clone https://github.com/Team-0230/api-gateway-springboot.git
   ```

2. Navigate to the project directory:

   ```
   cd api-gateway-springboot
   ```

3. Build the project using Maven:

   ```
   mvn clean install
   ```

4. Run the application:

   ```
   mvn spring-boot:run
   ```

5. The API Gateway will start running on port 8080 by default. You can configure the port in the `application.yml` file.

## Configuration

The configuration for the API Gateway can be found in the `application.yml` file located in the project's resources directory. You can modify the properties to customize the behavior of the gateway, such as route configurations, service URLs, and instance preferences.

### Registering and Using a New Service

To register and use a new service with the API Gateway, follow these steps:

1. Add a new route configuration under the `eureka.client.routes` section in the `application.yml` file. For example:

   ```yaml
   eureka:
     client:
       routes:
         - id: service1-route
           uri: lb://service1
           predicates:
             - Path=/service1/**
   ```

   Replace `service1-route` with a unique identifier for the route. Modify `service1` to match the registered name of the new service. Customize the predicates as per your requirements.

2. Save the changes to the `application.yml` file.

3. Restart the API Gateway for the changes to take effect.

4. The new service will now be accessible through the API Gateway using the specified route. For example, if the route configuration is `/service1/**`, the new service can be accessed at `http://localhost:8080/service1/`.

For more information on configuring and using the API Gateway, refer to the [official documentation](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/).

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvement, please open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgements

This project utilizes the Spring Cloud Gateway library for building the API Gateway.
