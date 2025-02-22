---
title: Jenkins troubleshooting
description: This article describes how to troubleshoot the most common problems with the jenkins scheulder
template: troubleshooting-guide-template
---

When deploying an application, Jenkins does not restart properly and the `Deploy_Scheduler` deployment step fails. 

## Cause

Jenkins does not have enough resources to process a long-running heavy job and, subsequently, cannot follow the stop command during a deployment.

## Solution

Before deploying an application, stop long-running, heavy jobs. In the *Build Executor Status* section of the Jenkins Web UI, select **x** next to each long-running job.
