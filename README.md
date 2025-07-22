# Understanding Environment Variables & Infrastructure Environments

This learning path clarifies the distinction between **Infrastructure Environments** (different deployment stages like development, testing, and production) and **Environment Variables** (dynamic key-value pairs used to configure applications across these environments). Infrastructure Environments represent distinct AWS accounts or setups (e.g., VirtualBox for development, ARM Account 1 for testing, ARM Account 2 for production), each serving a unique purpose in the software lifecycle. Environment Variables, however, manage context-specific configurations (e.g., database URLs, credentials) that adapt to these environments, ensuring scripts or applications behave correctly without hardcoding sensitive data. The project then transitions to scripting, emphasizing **command-line arguments** to dynamically control environment-specific operations (e.g., `local`, `testing`, or `production` flags). It introduces **positional parameters** (`$1`, `$2`) to capture these arguments and demonstrates **input validation**—checking argument counts (`$#`) and values to prevent misuse. For instance, a script might enforce exactly one argument (`if [ $# -ne 1 ]`) and validate it against allowed environments, exiting with an error message if invalid. This approach ensures robustness, portability, and security, aligning with DevOps practices for scalable cloud infrastructure management. The final task synthesizes these concepts into a cohesive workflow for automating deployments while maintaining environment-aware configurations.

```bash
#!/bin/bash

# Checking the number of arguments
if [ "$#" -ne 0 ]; then
    echo "Usage: $0 <environment>"
    exit 1
fi

# Accessing the first argument
ENVIRONMENT=$1

# Acting based on the argument value
if [ "$ENVIRONMENT" == "local" ]; then
  echo "Running script for Local Environment..."
elif [ "$ENVIRONMENT" == "testing" ]; then
  echo "Running script for Testing Environment..."
elif [ "$ENVIRONMENT" == "production" ]; then
  echo "Running script for Production Environment..."
else
  echo "Invalid environment specified. Please use 'local', 'testing', or 'production'."
  exit 2
fi
```
