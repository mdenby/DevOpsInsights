---

copyright:
  years: 2016, 2018
lastupdated: "2018-8-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Getting started tutorial
{: #gettingstarted}

{{site.data.keyword.DRA_full}} applies developer, team, and deployment analytics to your busiest DevOps projects. Use it to learn how compliant your team is with DevOps and developer practices, to manage risk in your codebase, and to automatically enforce quality standards in continuous delivery projects. 
{:shortdesc}

{{site.data.keyword.DRA_short}} is available only in the US South region.
{: tip}

To use {{site.data.keyword.DRA_short}}, you must add it to a toolchain. Many toolchain templates already include {{site.data.keyword.DRA_short}}. Be sure to also [add it to your {{site.data.keyword.Bluemix_notm}} resource group or org as a service](/docs/services/reqnsi.html) so that you can see information about {{site.data.keyword.DRA_short}} and access some of the toolchain templates that include it from your {{site.data.keyword.Bluemix_notm}} dashboard.  

## Step 1: Add DevOps Insights to a toolchain
{: #catalog}

{{site.data.keyword.DRA_short}} is available through integration with {{site.data.keyword.contdelivery_full}} toolchains. You can add {{site.data.keyword.DRA_short}} to any toolchain by selecting it from the tool integration catalog.

{{site.data.keyword.DRA_short}} is part of many toolchain templates. If you create a toolchain from a template that includes {{site.data.keyword.DRA_short}}, make sure that {{site.data.keyword.DRA_short}} is set to **Advanced**. Then, create the toolchain and skip to [Step 2](/docs/services/DevOpsInsights/index.html#using).
{: tip}

1. Click **Add a Tool**.

2. Click **{{site.data.keyword.DRA_short}}**.

3. Click **Create Integration**.

{{site.data.keyword.DRA_short}} is now available on your toolchain's Overview page. Your repo and issue-tracking system are scanned automatically for data. 

## Step 2: Explore your project's data
{: #using}

If your toolchain includes GitHub, GitLab, or JIRA, {{site.data.keyword.DRA_short}} automatically provides you with information about your codebase and team after some initial data gathering and analysis. If your toolchain does not include any of those integrations, add one of them.
{: tip}

1. From your toolchain's Overview page, click **{{site.data.keyword.DRA_short}}**.

2. Click **Team** or **Developer Insights** and then choose a data category. 

3. Explore your project's data by viewing the dashboards in the data category. If you want to know more about a graph or what you might do with its information, click **Information** or **Guidance**.

## Next steps
{: #next_steps}

After you explore Team and Developer Insights, configure [Deployment Risk](/docs/services/DevOpsInsights/about_risk.html) to help you enforce code quality. Deployment Risk is compatible with both Delivery Pipeline for {{site.data.keyword.contdelivery_short}} and Jenkins.
