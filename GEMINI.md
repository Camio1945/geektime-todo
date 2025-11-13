# Project: Geektime Todo

This project is a "Todo" application built with Java and Gradle. It is structured as a multi-module project with a core domain module, a REST API, and a command-line interface (CLI).

## Modules

*   `todo-core`: Contains the core business logic and domain models for the Todo application.
*   `todo-api`: A RESTful API built using Spring Boot, Spring Data JPA, and backed by a MySQL database. It uses Flyway for database migrations.
*   `todo-cli`: A command-line interface for interacting with the Todo application, built with Picocli.

## Building and Running

### Prerequisites

*   Java (version specified in `gradle.properties` if present, otherwise a recent LTS version is a safe bet)
*   Gradle (the project uses a wrapper, so you don't need to install it separately)
*   MySQL database for the `todo-api` module.

### Common Gradle Tasks

*   **Build the entire project:**
    ```bash
    ./gradlew build
    ```

*   **Run checks (style, tests):**
    ```bash
    ./gradlew check
    ```

*   **Run the REST API (development mode):**
    ```bash
    ./gradlew :todo-api:bootRun
    ```
    The API will be available at `http://localhost:8080`.

*   **Run database migrations:**
    ```bash
    ./gradlew migrate
    ```
    This will apply migrations to both `todo_dev` and `todo_test` databases.

*   **Create a runnable JAR for the CLI:**
    ```bash
    ./gradlew uberJar
    ```

*   **Run the CLI:**
    ```bash
    java -jar todo-cli/build/libs/todo-uber-*.jar [commands]
    ```

## Development Conventions

### Code Style

The project uses Checkstyle to enforce a consistent code style. The configuration can be found in `gradle/config/checkstyle/sun_checks.xml`. You can run the style checks with:

```bash
./gradlew check
```

### Testing

*   **Unit Tests:** Standard JUnit tests are used across the modules.
*   **Integration Tests:** The `todo-api` module uses Cucumber for behavior-driven development (BDD). The feature files are located in `todo-api/src/test/resources/features`.

You can run all tests with:

```bash
./gradlew test
```
