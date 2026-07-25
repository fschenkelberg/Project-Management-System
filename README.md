# Project Management System

A comprehensive project management application built with Spring Boot, featuring a robust backend API and modern development practices.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Project Setup](#project-setup)
- [Running the Application](#running-the-application)
- [Verifying the Application](#verifying-the-application)
- [Project Structure](#project-structure)
- [Troubleshooting](#troubleshooting)
- [Development Workflow](#development-workflow)
- [Next Steps](#next-steps)
- [Support & Documentation](#support--documentation)

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- **Java 21 LTS** - [Download](https://www.oracle.com/java/technologies/downloads/#java21)
- **Git** - [Download](https://git-scm.com/)
- **IDE** (Optional but recommended):
  - Visual Studio Code with Java extensions

## Project Setup

### 1. Clone the Repository

```bash
git clone https://github.com/fschenkelberg/Project-Management-System.git
cd Project-Management-System
```

### 2. Verify Java Installation

```bash
java --version
# Expected output: openjdk version "21.x.x" or similar
```

### 3. Build the Project

The project uses Gradle Wrapper, so no separate Gradle installation is required.

**On Windows:**

```bash
./gradlew clean build
```

This command will:

- Clean any previous build artifacts
- Download all dependencies
- Compile the source code
- Run tests
- Create an executable JAR file in `build/libs/`

### 4. Verify the Build

After a successful build, you should see:

```
BUILD SUCCESSFUL in Xs
```

## Running the Application

### Option 1: Using Gradle (Recommended for Development)

**On Windows:**

```bash
./gradlew bootRun
```

The application will start and display output similar to:

```
2024-01-XX XX:XX:XX.XXX  INFO XXXX --- [  restartedMain] c.m.p.ProjectManagementApplication     : Started ProjectManagementApplication in X.XXX seconds (JVM running for X.XXX)
```

### Option 2: Using the Executable JAR

```bash
# Build the project first
./gradlew clean build

# Run the JAR file
java -jar build/libs/project-management-0.0.1-SNAPSHOT.jar
```

### Option 3: Running in Your IDE

**Visual Studio Code:**

1. Open the project root directory
2. Install the "Extension Pack for Java" extension
3. Open `src/main/java/com/mycompany/projectmanagement/ProjectManagementApplication.java`
4. Click the **Run** button above the main method

## Verifying the Application

### Check Application Health

Once the application is running, verify it's working correctly:

```bash
curl http://localhost:8080/actuator/health
```

Expected response:

```json
{
  "status": "UP"
}
```

### Check Application Info

```bash
curl http://localhost:8080/actuator/info
```

### Available Actuator Endpoints

- **Health:** `http://localhost:8080/actuator/health`
- **Metrics:** `http://localhost:8080/actuator/metrics`
- **Environment:** `http://localhost:8080/actuator/env`

## Project Structure

```
Project-Management-System/
├── gradle/                          # Gradle wrapper files
├── src/
│   ├── main/
│   │   ├── java/com/mycompany/projectmanagement/
│   │   │   └── ProjectManagementApplication.java
│   │   └── resources/
│   │       ├── application.properties
│   │       └── application.yml
│   └── test/
│       └── java/com/mycompany/projectmanagement/
├── build.gradle                     # Gradle build configuration
├── gradlew                          # Gradle Wrapper (macOS/Linux)
├── gradlew.bat                      # Gradle Wrapper (Windows)
├── settings.gradle                  # Gradle settings
└── README.md
```

## Troubleshooting

### Issue: Java Version Mismatch

**Error:** `Exception in thread "main" java.lang.UnsupportedClassVersionError`

**Solution:**

```bash
java --version
# Ensure you have Java 21 LTS installed
```

### Issue: Gradle Build Fails

**Error:** `Build failed with an exception`

**Solution:**

```bash
# Clean and retry
./gradlew clean build --refresh-dependencies
```

### Issue: Port 8080 Already in Use

**Error:** `Address already in use`

**Solution:**
Either stop the process using port 8080 or change the port in `application.properties`:

```properties
server.port=8081
```

### Issue: Dependency Download Failures

**Error:** `Could not resolve dependencies`

**Solution:**

```bash
# Clear the Gradle cache and retry
rm -rf ~/.gradle/caches
./gradlew clean build
```

## Development Workflow

### Building Without Running

```bash
./gradlew build
```

### Running Tests

```bash
./gradlew test
```

### Checking for Build Issues

```bash
./gradlew check
```

### Stopping the Application

If running with `bootRun`, press **Ctrl+C** (or **Cmd+C** on macOS) in the terminal.

## Next Steps

- Review the [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- Add your first REST endpoint
- Configure database connectivity
- Set up authentication and authorization

## Support & Documentation

- **Spring Boot:** https://spring.io/projects/spring-boot
- **Gradle:** https://gradle.org/
- **Java 21 LTS:** https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html
- **Project Repository:** https://github.com/fschenkelberg/Project-Management-System

---

For issues or questions, please refer to the project's issue tracker.
