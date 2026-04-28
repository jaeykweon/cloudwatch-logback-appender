# Validation Branch for fix/mdc

This branch contains the code fix to ensure MDC values are properly delivered to CloudWatch logs, along with a test case to validate it.

In the original code, when MDC values are used in the `CloudWatchAppender` pattern (e.g. `[%X{traceId}]`), no logs are written to CloudWatch at all (verified with LocalStack).

The code fix is in the `fix/mdc` branch (intended for PR). This branch (`validate/mdc`) contains the test case and LocalStack environment setup for validating the fix locally.

Validation is done by simulating the AWS CloudWatch Logs service locally using LocalStack. 

After running the `mdcCase` test in `CloudWatchAppenderRealTest`, it is confirmed by checking whether `AWS logs.PutLogEvents` logs are generated in the Docker LocalStack container logs.

A LocalStack setup for testing CloudWatch locally is provided in `docker-compose.yml`.
