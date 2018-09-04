---

copyright:
  years: 2018
lastupdated: "2018-9-4"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

<!-- Name your file `at-events.md` and include it in the Reference nav group in your toc file. -->

# {{site.data.keyword.cloudaccesstrailshort}} events
{: #at_events}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with the {{site.data.keyword.DRA_short}} service in {{site.data.keyword.Bluemix}}. 
{: shortdesc}

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.Bluemix_notm}}. For more information, see the [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla).

<!-- You can create different sections to group events by area. -->

## List of events
{: #events}

The following table lists the actions that generate an event:

| Action | Description | 
|:-----------------|:-----------------|
| devopsinsights.toolchain.alldata.delete | Delete {{site.data.keyword.DRA_short}} data. This action records the number of records that were deleted and which filter was used to delete the data. | 
| toolchain.tool-instance.deploy |  Create a tool integration. The **target.name** field shows the name of the tool integration to add to the toolchain. For example, draservicebroker.  |
| toolchain.tool-instance.undeploy | Delete a tool integration. The **target.name** field shows the name of the tool integration to delete from the toolchain. For example, draservicebroker.  |
{: caption="Table 1. Actions that generate events" caption-side="top"}

## Where to view the events
{: #ui}

<!-- For example, choose one of the following two options. -->

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} **account domain** that is available in the {{site.data.keyword.Bluemix_notm}} region where the events are generated.
