---
layout: documentation
title: Monitoring
---

Monitoring should be setup for all of the Cerberus services with the tools used by your organization.

# Health Check Lambda

A <a target="_blank" onclick="trackOutboundLink('https://github.com/Nike-Inc/cerberus-healthcheck-lambda')" href="https://github.com/Nike-Inc/cerberus-healthcheck-lambda">Health Check Lambda</a> provides an end-to-end test of the 
general health of the production Cerberus environment. It checks that a lambda can authenticate with Cerberus which 
will exercise the Cerberus Management Service (CMS) and its RDS DB. It then uses that auth token to read from the 
healthcheck SDB which will exercise and test that [Vault](../architecture/vault) and Consul are up and 
running.  The lambda can be invoked via the AWS API Gateway.

# HTTP Metrics

Monitoring HTTP response codes for the Gateway and CMS gives a good indication of health and activity within the system, e.g. aggregating data from /var/log/nginx/access.log and displaying on a dashboard.

# References

* <a target="_blank" onclick="trackOutboundLink('https://github.com/Nike-Inc/cerberus-healthcheck-lambda')" href="https://github.com/Nike-Inc/cerberus-healthcheck-lambda">Health Check Lambda Github</a>
* <a target="_blank" onclick="trackOutboundLink('https://aws.amazon.com/lambda/')" href="https://aws.amazon.com/lambda/">AWS Lambda</a>
* <a target="_blank" onclick="trackOutboundLink('https://aws.amazon.com/api-gateway/')" href="https://aws.amazon.com/api-gateway/">AWS API Gateway</a>
* <a target="_blank" onclick="trackOutboundLink('https://aws.amazon.com/rds/')" href="https://aws.amazon.com/rds/">Amazon Relational Database Service (RDS)</a>