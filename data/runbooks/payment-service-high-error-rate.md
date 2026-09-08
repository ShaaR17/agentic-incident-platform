# Payment Service - High Error Rate Runbook

## Purpose

This runbook provides troubleshooting steps for high error rates in the payment service.

## Symptoms

Common symptoms include:

- Payment API returning HTTP 500 errors
- Increased payment request latency
- Database connection errors
- Database connection pool utilization above 90%

## Investigation

### Step 1 - Check application logs

Search payment-service logs for:

- Connection pool exhausted
- Failed to acquire database connection
- Database connection timeout

### Step 2 - Check database connection pool

Check:

- Active database connections
- Maximum connection pool size
- Connection pool utilization

If utilization reaches 100%, investigate connection exhaustion.

### Step 3 - Check database health

Verify:

- Database availability
- Database CPU
- Database memory
- Active connections

## Possible Causes

1. Database connection leak
2. Database overload
3. Connection pool configured too small
4. Sudden increase in traffic

## Remediation

If the connection pool is exhausted:

1. Confirm database health.
2. Restart the payment service if connections are stuck.
3. Increase the connection pool size if traffic requires it.
4. Monitor error rate after remediation.

## Verification

After remediation:

- Error rate should return below 5%.
- Database connection utilization should remain below 80%.
- Payment requests should return HTTP 200.