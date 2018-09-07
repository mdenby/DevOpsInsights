---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# About DevOps Insights

{{site.data.keyword.DRA_short}} provides a wealth of information about your tests, builds, and deployments to prevent risky code from being deployed. You can use it to automate quality protection in your delivery pipeline by using policies and gates. It also provides trend information about your builds, deployments, and tests to understand changes over time.
{:shortdesc}

## Quality Dashboard

The Quality Dashboard provides an overview of the tests results for your applications. The dashboards are automatically populated with the most recent information from your pipelines' {{site.data.keyword.DRA_short}} tests. You can view trending information about your tests over time to understand how they have historically performed. Drill down into each build to understand the risk to deploy the code to production.

## Risk Analysis

Risk Analysis provides an overview of the risks associated with deploying code in your applications or environments. You can drill down to see a risk assessment, add a policy and rules to ensure risky code is not deployed. 

## Deployment Frequency

Deployment Frequency shows trends for your production, staging, or other environments. This view also shows deployment success and failures. Click a particular deployment to view more details about it. If you're on an agile team, you should see the deployment frequency trend upward over time.

## Policies

Policies are sets of rules that control the gates in your delivery pipeline. If your code does not meet or exceed a policy that is enacted at a particular gate, the deployment is halted to prevent risky code from being released.

## Build Frequency

Build Frequency shows trends for your long-running branches. This view also shows build successes and failures. You can select individual builds to see more details. If you're on an agile team, you want to see a lot of daily builds on the integration branch. Otherwise, your team is not merging their code frequently.

## Quality Trends

You can view trends for tests for the builds that are from a certain branch or are deployed to a certain environment. For example, you can see test trends for builds from the master branch. If some tests fail for builds that went to production, you might want to take some action. Also, if the number of tests are dwindling over time, that might be a cause for concern. Tests types that are supported include: functional verification tests, unit tests, code coverage, static app scan, dynamic app scan, and SonarQube. 

## Prerequisites
{: #prerequisites}

Deployment Risk requires some configuration beyond what is described in [Getting Started with {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).

To use Deployment Risk, you need two things:

* An instance of {{site.data.keyword.deliverypipeline}} or a Jenkins project
* Tests that you want to use to evaluate your project

## Integration information

DevOps Insights integrates with {{site.data.keyword.deliverypipeline}}, which is part of {{site.data.keyword.contdelivery_full}}, and with Jenkins projects. At a high level, the instructions for using either are similar.

If you are using {{site.data.keyword.deliverypipeline}}, follow the instructions for Integrating {{site.data.keyword.DRA_short}} with Continuous Delivery (link). This will show you how to prepare your pipeline, create or edit test jobs for {{site.data.keyword.DRA_short}} to receive results, and add policies and gates.

If you are a Jenkins user, follow the instructions for Integrating with Jenkins 
(https://wiki.jenkins.io/display/JENKINS/IBM+Cloud+DevOps+Plugin). This will show you how to install and configure the Jenkins plugin, publish build and deployment records, and publish test results.{:new_window: target="_blank"}
