---
name: deploy-platform
description: Use when deploying to Platform. Covers setup, configuration, and best practices for production deployments.
version: 1.0.0
author: Your Name
---

# Deploying to [Platform]

## Description
Guide for deploying applications to [Platform or Repository], including configuration, CI/CD setup, and monitoring.

## When to Use
Use this skill when:
- Setting up new deployments
- Configuring CI/CD pipelines
- Troubleshooting deployment issues

## Prerequisites
- Account on [Platform]
- CLI tool installed
- Access credentials configured

## Initial Setup

### 1. Install CLI
```bash
# Installation command
```

### 2. Authenticate
```bash
platform login
```

### 3. Create Project
```bash
platform create my-project
```

## Configuration

### Project Configuration
```yaml
# platform.yml
name: my-project
region: us-east-1
runtime: nodejs-18
build:
  command: npm run build
  output: dist
env:
  NODE_ENV: production
```

### Environment Variables
```bash
platform env set DATABASE_URL="..."
platform env set API_KEY="..."
```

## Deployment Commands

### Deploy to Production
```bash
platform deploy --prod
```

### Deploy to Preview
```bash
platform deploy --preview
```

### Rollback
```bash
platform rollback [deployment-id]
```

## CI/CD Integration

### GitHub Actions
```yaml
name: Deploy
on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Deploy
        run: platform deploy --prod
        env:
          PLATFORM_TOKEN: ${{ secrets.PLATFORM_TOKEN }}
```

## Monitoring

### Health Checks
```bash
platform health check
```

### View Logs
```bash
platform logs --follow
```

### Metrics
```bash
platform metrics --last 24h
```

## Troubleshooting

### Build Failures
1. Check build logs: `platform logs --build`
2. Verify dependencies are installed
3. Check for missing environment variables

### Runtime Errors
1. Check application logs: `platform logs`
2. Verify environment variables
3. Check resource limits

## Best Practices
1. Use preview deployments for testing
2. Set up automated health checks
3. Configure alerts for failures
4. Keep secrets in environment variables
5. Use blue-green deployments for zero downtime
