# Getting Started with Logging

The `opensourceleg` library provides an easy-to-use yet powerful logging system that helps you track what's happening in your application. Whether you're debugging issues, monitoring performance, or collecting data, our logging system has you covered.

## Overview

Our `Logger` class builds upon Python's native `logging` module and adds several powerful features:

- **Data Logging**: Easily track variables and measurements over time
- **Flexible Output**: Write to both console and files simultaneously
- **Thread Safety**: Safe to use in multi-threaded applications
- **Singleton Pattern**: One logger instance across your entire application

## Quick Start

### 1. Create Your Logger

First, create a logger instance in your Python file:

```python
from opensourceleg.logging import Logger, LogLevel

logger = Logger(
    log_path="./logs",
    file_name="my_application"
)
```

### 2. Start Logging!

It's as simple as:

```python
# Log some basic information
logger.info("Application started")

# Log when something might be wrong
logger.warning("Battery level below 20%")

# Log errors when they occur
logger.error("Failed to connect to sensor")
```

### 3. Understanding Log Levels

We provide five log levels, from least to most severe:

```python
# For detailed debugging information
logger.debug("Motor position: 123.4 degrees")

# For general information
logger.info("Robot initialized successfully")

# For potential issues
logger.warning("Battery running low")

# For serious problems
logger.error("Failed to read sensor data")

# For fatal errors
logger.critical("System shutdown required")
```

### 4. Customizing Your Logger

You can configure the logger to match your needs:

```python
logger = Logger(
    log_path="./logs",          # Where to save your log files
    file_name="robot_test",     # Name your log files (e.g., robot_test_2024_03_20.log)
    buffer_size=1000,           # Save to file every 1000 entries
    console_level=LogLevel.INFO # Show INFO and above in console
)
```

## Understanding Logger Instances

Our logging system uses a singleton pattern, which means there's only one logger instance per configuration. Here's how to properly use it in your applications:

### Creating Your Own Logger (Recommended)

```python
from opensourceleg.logging import Logger

# Create your own logger instance
logger = Logger(
    log_path="./logs",
    file_name="my_experiment"
)

# Use your logger instance throughout your application
logger.info("Application started")
logger.debug("Configuration loaded")
```

### About the Global Logger (For Internal Use)

The library includes a global `LOGGER` instance, but this is primarily for internal library use:

```python
from opensourceleg.logging import LOGGER  # Meant for library internal use

# Prefer creating your own logger instance instead of using LOGGER directly
```

## Best Practices

1. **Use Appropriate Log Levels**

    - `DEBUG`: Detailed information for debugging
    - `INFO`: General operational messages
    - `WARNING`: Something unexpected but not critical
    - `ERROR`: Something failed but application continues
    - `CRITICAL`: Application cannot continue

2. **Include Relevant Details**

    ```python
    logger.error(f"Sensor read failed: {sensor_id}, Error: {error_message}")
    ```

    f-strings are preferred over string interpolation. This is because they are more readable and easier to debug.

3. **Log Early, Log Often**

    - Better to have too much information than too little
    - You can always filter logs later

## Next Steps

Ready to dive deeper? Check out these tutorials:

1. [Configuring the Logger](configuring_logger.md) - Learn all configuration options
2. [Logging Data](logging_data.md) - Master data logging and analysis
3. [API Reference](../../api/logging.md) - Complete API documentation

Need help? Join our community discussion or open an issue on GitHub!
