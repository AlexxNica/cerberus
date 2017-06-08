---
layout: documentation
title: Roadmap
---

-  Develop Cerberus client compatibility matrix - we'd like to develop a compatibility matrix describing what it means 
   to be a 'Cerberus client' in a language neutral way and the features/gaps of each existing client.
-  Improve cross-region back-up and recovery process
-  Make Cerberus easier to use and deploy for other companies
   -  Pre-built AMIs, automation, improved documentation, work with early adopters
   -  Simplify environment creation by defining Cerberus environment in YAML and adding composite commands
   -  Automate TLS Certificate setup using Let's Encrypt (this would eliminate the most manual and error prone steps in creating an environment)
-  Add additional commands to CLI for rotation of:
   -  TLS Certificates
   -  Vault Root token
   -  CMS token
   -  Vault Master Key and Unseal Keys, e.g. Rekey command
   -  Backend encryption key, e.g. Rotate command
-  SOX/PCI compliance - ensure the proper auditing capabilities are in place to support compliance, i.e. change tracking, etc.
-  Ubuntu - remove tight coupling to particular release (14.04LTS) or at least upgrade to 16LTS.
-  Stay up-to-date with latest versions of Vault and Consul
-  Consider the new STS IAM Auth Endpoint (could eliminate KMS from our auth flow, potentially cheaper, less complicated, faster, etc)
-  Consider AWS Shield to replace existing Edge Security
-  Increase horizontal scalability (consider replacing Vault or adopting new Vault features)

