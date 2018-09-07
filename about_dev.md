---

copyright:
  years: 2016, 2018
lastupdated: "2018-3-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# About Code (Beta)
{: #gettingstarted}

{{site.data.keyword.DRA_full}} Developer Insights provides a comprehensive way to explore your project’s development risk. You can identify files with high error proneness and get a compliance view of the project against DevOps practices.
{:shortdesc}

After you open {{site.data.keyword.DRA_short}} from your toolchain, click **Developer Insights**. From there, you can select an analytic category to dive deeper into your project's codebase. What each set of data indicates can vary from team to team, and you can drill down into each visualization for help and guidance. You can filter the data by date, as well as many other criteria.

## Data categories
The data that {{site.data.keyword.DRA_short}} uses to populate its dashboards is mined automatically from your team's source-control repository. You can get more information about what the data means and how you can apply it to your project by clicking **Information** or **Guidance** on the Best Practices charts. You can also look at the Findings and Details that are part of the other visualizations for more information.

### Developer best practices

Developer Insights provides a number of charts that measure your project against good DevOps and developer practices. Use this category to get a high-level view of your project's maturity, health, and efficiency.

### Issues

The Issues category displays all of your team's work-tracking issues in one place. The issues are automatically grouped by type, priority, and tag, and can be shown over time.

These issue groupings can vary in meaning from team to team. One team might want to know whether most items that are tagged for a particular release are closed, while another team might not tag releases and instead work according to open-issue priority.  

### Commits

The Commits category displays all of your team's commits in one place. The commits are automatically grouped by type, tag, and line changes. You can see them over a period of time that you choose.

Commits indicate the work that your team members are contributing to your codebase. Examine your commit data to understand where effort is being expended historically and how you can better balance your team members' workloads.

### Files

The Files category shows which of your project's files are the busiest. Whether by number of line changes, commits, or defects, this data indicates where your team is most active.

Generally, try to reduce both the number of hands that touch a file and that file's change frequency. This goal might be impossible with certain files, such as common configuration files. However, many developers making many changes to the same file at the same time is a recipe for trouble.

### Pull requests

The Pull requests category shows you your team's pull requests in one place.  The pull requests are evaluated for error proneness using machine learning.  You can quickly see what pull requests are adding risk to your codebase.

Pull requests display the work your team members are attempting to merge into your codebase.  Examine your pull request data to understand all the risk associated with it and how you can reduce risk in the future.

## File extension filtering

DevOps Insights ignores files that have these extensions:

* .bin
* .cdr
* .jpeg
* .jpg
* .json
* .markdown
* .md
* .png
* .pyc
* .svg
* .text
* .yaml
* .yml
