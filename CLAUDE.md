# CLAUDE.md - AI Assistant Guide for mention-system

## Project Overview

**Project Name**: mention-system
**Version**: 1.0-SNAPSHOT
**Package**: com.example.mention
**Type**: Java Maven Application
**Current State**: Early-stage skeleton/template project

### Purpose
This is a minimal Maven-based Java application intended to become a mention system (e.g., for handling @mentions in a social platform or chat context). Currently contains only placeholder "Hello World" code and requires implementation of core functionality.

---

## Repository Structure

```
mention-system/
├── README.md                                    # Project documentation (minimal)
├── pom.xml                                      # Maven build configuration
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── example/
│   │               └── mention/
│   │                   └── App.java             # Main application entry point
│   └── test/
│       └── java/
│           └── com/
│               └── example/
│                   └── mention/
│                       └── AppTest.java         # JUnit test suite
└── target/                                      # Build output (generated)
```

### Key Files

| File | Purpose | Reference |
|------|---------|-----------|
| `pom.xml` | Maven build configuration, dependencies, project metadata | Root |
| `src/main/java/com/example/mention/App.java` | Main application class with entry point | App.java:9 |
| `src/test/java/com/example/mention/AppTest.java` | Unit test suite using JUnit 3.8.1 | AppTest.java:10 |
| `README.md` | Project documentation | Root |

---

## Technology Stack

### Languages & Runtime
- **Java**: OpenJDK 21.0.8
- **Build Tool**: Apache Maven 3.9.11
- **Packaging**: JAR (Java Archive)

### Dependencies
- **JUnit 3.8.1** (test scope only) - Testing framework

### Build Configuration
- **Group ID**: com.example.mention
- **Artifact ID**: mention-system
- **Version**: 1.0-SNAPSHOT
- **Packaging**: jar

---

## Development Workflows

### Building the Project

```bash
# Clean previous builds
mvn clean

# Compile source code
mvn compile

# Run tests
mvn test

# Package into JAR
mvn package

# Install to local Maven repository
mvn install

# Full build cycle (clean, compile, test, package)
mvn clean package
```

### Running the Application

```bash
# After building (creates target/mention-system-1.0-SNAPSHOT.jar)
java -jar target/mention-system-1.0-SNAPSHOT.jar

# Or run directly with Maven
mvn exec:java -Dexec.mainClass="com.example.mention.App"
```

### Testing

```bash
# Run all tests
mvn test

# Run specific test class
mvn test -Dtest=AppTest

# Run tests with detailed output
mvn test -X
```

---

## Code Conventions

### Package Structure
- **Base package**: `com.example.mention`
- **Main source**: `src/main/java/com/example/mention/`
- **Test source**: `src/test/java/com/example/mention/`

### Naming Conventions
- **Classes**: PascalCase (e.g., `App`, `AppTest`)
- **Methods**: camelCase (e.g., `main`, `testApp`)
- **Test classes**: Suffix with `Test` (e.g., `AppTest`)
- **Test methods**: Prefix with `test` (e.g., `testApp`)

### Code Style
The existing codebase follows standard Java conventions:
- 4-space indentation
- Opening braces on same line
- Javadoc comments for classes and methods
- Standard Maven directory layout

### Testing Conventions
- **Framework**: JUnit 3.8.1 (legacy version)
- **Test class**: Extends `TestCase`
- **Test suite**: Uses `TestSuite` pattern
- **Test methods**: Must be public, return void, start with "test"
- **Assertions**: Use JUnit assertion methods (assertTrue, assertEquals, etc.)

---

## Current Implementation Status

### Implemented
✅ Basic Maven project structure
✅ Main application entry point (App.java:9)
✅ JUnit test framework setup (AppTest.java:10)
✅ Git version control
✅ Build configuration (pom.xml)

### Not Yet Implemented
❌ Actual mention parsing/processing logic
❌ Data models for mentions
❌ Storage/persistence layer
❌ API or interface definitions
❌ Comprehensive tests
❌ Complete documentation
❌ Configuration management
❌ Logging framework

---

## Key Conventions for AI Assistants

### When Working with This Codebase

1. **Maven First**: Always use Maven commands for building and testing
   - Don't try to compile Java files manually with `javac`
   - Use `mvn compile`, `mvn test`, `mvn package`

2. **Package Structure**: Maintain the existing package structure
   - All new classes should be in `com.example.mention` or sub-packages
   - Follow the standard Maven directory layout

3. **Testing**: Write tests for new functionality
   - Create test classes in `src/test/java/com/example/mention/`
   - Extend `TestCase` and follow JUnit 3.8.1 patterns
   - Run tests before committing changes

4. **Dependencies**: Add new dependencies to pom.xml
   - Always specify version numbers
   - Use appropriate scope (compile, test, provided, runtime)
   - Consider updating to newer versions (e.g., JUnit 4 or 5)

5. **Documentation**: Update documentation as you make changes
   - Add Javadoc comments to new classes and public methods
   - Update README.md with usage instructions
   - Update this CLAUDE.md if project structure changes

6. **Git Workflow**: Follow the specified branch conventions
   - Current branch: `claude/claude-md-mhy2z9uv5dmn0hya-019QxqacsFn9B9n5fR7yMdSv`
   - Use descriptive commit messages
   - Push to the correct branch with `git push -u origin <branch-name>`

### Common Development Tasks

#### Adding a New Class
1. Create file in `src/main/java/com/example/mention/`
2. Use package declaration: `package com.example.mention;`
3. Add Javadoc comments
4. Create corresponding test in `src/test/java/com/example/mention/`
5. Run `mvn compile` to verify
6. Run `mvn test` to verify tests pass

#### Adding a New Dependency
1. Open `pom.xml`
2. Add dependency in `<dependencies>` section
3. Specify groupId, artifactId, version, and scope
4. Run `mvn clean install` to download and verify

#### Refactoring Code
1. Run existing tests first: `mvn test`
2. Make changes
3. Run tests again to ensure nothing broke
4. Update tests if behavior changed
5. Update documentation if interfaces changed

---

## Architecture Overview

### Current Architecture
```
┌─────────────────────────────────┐
│  mention-system (JAR)           │
│  com.example.mention            │
└──────────┬──────────────────────┘
           │
      ┌────▼────────┐
      │   App.java  │
      │   (Main)    │
      │             │
      │ - main()    │
      │ - Prints    │
      │   "Hello"   │
      └─────────────┘
```

### Recommended Future Architecture
```
┌─────────────────────────────────────────┐
│  mention-system                         │
├─────────────────────────────────────────┤
│  Presentation Layer                     │
│  - CLI/API Interface                    │
├─────────────────────────────────────────┤
│  Business Logic Layer                   │
│  - MentionParser                        │
│  - MentionProcessor                     │
│  - NotificationService                  │
├─────────────────────────────────────────┤
│  Data Layer                             │
│  - MentionRepository                    │
│  - UserRepository                       │
├─────────────────────────────────────────┤
│  Models                                 │
│  - Mention, User, Notification          │
└─────────────────────────────────────────┘
```

---

## Build Output

### Generated Artifacts
- **JAR file**: `target/mention-system-1.0-SNAPSHOT.jar`
- **Compiled classes**: `target/classes/`
- **Test classes**: `target/test-classes/`
- **Test reports**: `target/surefire-reports/`

### Clean Build
The `target/` directory is generated and should not be committed to version control. Always run `mvn clean` before major builds.

---

## Known Issues & Considerations

### Legacy Dependencies
- **JUnit 3.8.1** is outdated (released 2002)
  - Consider upgrading to JUnit 4.13.2 or JUnit 5 (Jupiter)
  - Current tests use old TestCase pattern

### Missing Configuration
- No compiler plugin version specified in pom.xml
  - Maven will use default, but explicit version is better practice
- No Java source/target version specified
  - Defaults to Java 7/8 depending on Maven version
  - Should specify for Java 21 compatibility

### Incomplete Implementation
- Current code is placeholder only
- No actual mention-system functionality exists
- Tests are trivial and don't validate real behavior

---

## Recommended Next Steps for Development

1. **Define Requirements**
   - What is a "mention"? (@username, #hashtag, etc.)
   - What operations are needed? (parse, store, notify, query)
   - What are the use cases?

2. **Design Data Models**
   - Create `Mention` class with fields (user, timestamp, content, etc.)
   - Create `User` class if needed
   - Define relationships between entities

3. **Implement Core Logic**
   - Create `MentionParser` to extract mentions from text
   - Create `MentionService` for business operations
   - Create repository/DAO classes for persistence

4. **Add Dependencies**
   - Consider logging framework (SLF4J + Logback)
   - Consider persistence (JPA/Hibernate, JDBC)
   - Consider JSON processing (Jackson, Gson)
   - Upgrade to modern JUnit version

5. **Expand Tests**
   - Write unit tests for each component
   - Add integration tests
   - Aim for >80% code coverage

6. **Update Documentation**
   - Write comprehensive README.md
   - Add API documentation
   - Create usage examples

---

## Environment Information

- **Operating System**: Linux 4.4.0
- **Java Version**: OpenJDK 21.0.8
- **Maven Version**: 3.9.11
- **Git**: Enabled
- **Working Directory**: `/home/user/mention-system`

---

## Git Branch Information

- **Current Branch**: `claude/claude-md-mhy2z9uv5dmn0hya-019QxqacsFn9B9n5fR7yMdSv`
- **Remote**: Local proxy at `http://127.0.0.1:20346/git/CesarChaMal/mention-system`

### Git Workflow for AI Assistants
1. Develop on the designated branch (starts with `claude/`)
2. Commit changes with clear, descriptive messages
3. Push with: `git push -u origin <branch-name>`
4. Branch name must match session ID or push will fail (403 error)
5. Retry network failures up to 4 times with exponential backoff (2s, 4s, 8s, 16s)

---

## Quick Reference Commands

```bash
# Build
mvn clean package                    # Full build
mvn compile                          # Compile only
mvn test                             # Run tests

# Run
java -jar target/mention-system-1.0-SNAPSHOT.jar

# Git
git status                           # Check status
git add .                            # Stage all changes
git commit -m "message"              # Commit
git push -u origin <branch>          # Push to remote

# Development
mvn clean install                    # Full build + install to local repo
mvn dependency:tree                  # Show dependency tree
mvn help:effective-pom              # Show effective POM with all defaults
```

---

## Contact & Support

For questions about this codebase or development practices, refer to:
- Project README.md (currently minimal)
- Maven documentation: https://maven.apache.org
- Java documentation: https://docs.oracle.com/en/java/

---

**Last Updated**: 2025-11-13
**Project Status**: Early Stage Development
**Code Maturity**: Template/Skeleton
