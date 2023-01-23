### Projects

- IDE's use projects, which specify the root directory of the codebase.
- This helps the IDE preform tasks like setting the classpath and automatically compiling code
- Basically, projects record metadata about the project.

### Building
- Ant build script creates executable project
- Ant build scripts are XML files
- Build targets are things that the script knows how to build
- Ant executes targets in order of execution that means no target is built before the target it depends on

### Tests
- Unit tests test the behaviour of a single code unit
- Functional tests test major functions that the system offers, and will typically involve the execution of many classes working together.

Release Pipeline Gateways:
- Code Review
- Coding standards/documentation procedures
- Automated tests
