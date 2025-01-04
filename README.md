# Payment Gateway System

A payment gateway system where users can transfer money from their wallet to other users' wallets. The system also includes a notification service to send wallet update emails to the users.

## Project Structure

The project is divided into multiple services:

- **common-lib**: Contains common utilities and DTOs used across other services.
- **notification-service**: Listens to Kafka topics and sends email notifications to users.
- **transaction-service**: Manages transactions between users.
- **user-service**: Manages user creation and user-related operations.
- **wallet-service**: Manages user wallets and processes wallet transactions.

## Services

### Common Library

- **RequestFilter**: A servlet filter to log request details.
- **DTOs**: Data Transfer Objects like `TransactionInitPayload`, `TransactionCompPayload`, and `UserCreatedPayload`.

### Notification Service

- **KafkaNotificationConsumerConfig**: Listens to the `USER_CREATED` Kafka topic and sends a welcome email to the user.
- **NotificationApp**: Main application class for the notification service.

### Transaction Service

- **TransactionKafkaConsumerConfig**: Listens to the `TXN_COMP` Kafka topic and updates transaction status.
- **TransactionKafkaProducerConfig**: Produces messages to Kafka topics.
- **TransactionService**: Handles transaction logic.
- **TransactionController**: REST controller for transaction-related endpoints.
- **TransactionApp**: Main application class for the transaction service.

### User Service

- **UserController**: REST controller for user-related endpoints.
- **UserService**: Handles user creation and logic.
- **UserApp**: Main application class for the user service.

### Wallet Service

- **KafkaConsumerConfig**: Listens to Kafka topics for user creation and transaction initiation.
- **WalletService**: Handles wallet-related logic and transactions.
- **WalletController**: REST controller for wallet-related endpoints.
- **WalletApp**: Main application class for the wallet service.

## Running the Project

1. **Build the project**:
    ```sh
    mvn clean install
    ```

2. **Run the services**:
    ```sh
    cd user-service
    mvn spring-boot:run

    cd ../wallet-service
    mvn spring-boot:run

    cd ../notification-service
    mvn spring-boot:run

    cd ../transaction-service
    mvn spring-boot:run
    ```

## Configuration

Each service has its own [application.properties](http://_vscodecontentref_/1) file for configuration. Ensure that the Kafka and MySQL configurations are correctly set up in these files.

## Dependencies

- Spring Boot
- Spring Kafka
- Spring Data JPA
- Lombok
- MySQL Connector

## License

This project is licensed under the MIT License.
