---

copyright:
  years: 2016, 2018
lastupdated: "2017-03-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Developer Insights
{: #gettingstarted}

{{site.data.keyword.DRA_full}} Developer Insights provides a comprehensive way to explore your project’s development risk. You can identify files with high error proneness and get a compliance view of the project against DevOps practices.
{:shortdesc}

After you open {{site.data.keyword.DRA_short}} from your toolchain, click **Developer Insights**. From there, you can select an analytic category to dive deeper into your project's codebase. What each set of data indicates can vary from team to team, and you can drill down into each visualization for help and guidance.

## Data categories
The data that {{site.data.keyword.DRA_short}} uses to populate its dashboards is mined automatically from your team's source-control repository. You can get more information about what the data means and how you can apply it to your project by clicking **Information** or **Guidance** on any chart.

### Developer Best Practices

Developer Insights provides a number of charts that measure your project against good DevOps and developer practices. Use this category to get a high-level view of your project's maturity, health, and efficiency.

### Issues

The Issues category displays all of your team's work-tracking issues in one place. The issues are automatically grouped by type, priority, and tag, and can be shown over time.

These issue groupings can vary in meaning from team to team. One team might want to know whether most items that are tagged for a particular release are closed, while another team might not tag releases and instead work according to open-issue priority.  

### Commits

Commits indicate the work that your team members are contributing to your codebase. Examine your commit data to understand where effort is being expended historically and how you can better balance your team members' workloads.

### Pull Requests

Pull requests shows the code that your team members are merging into another branch.  Dive into your pull request data to understand the risks associated with adding new code into your pristine code branch.

### Files

The Files category shows which of your project's files are the busiest. Whether by number of line changes, commits, authors, or defects, this data indicates where your team is most active. In addition, see where the risk lies with your files by reviewing the error proneness tab of files.

Generally, try to reduce both the number of hands that touch a file and that file's change frequency. This goal might be impossible with certain files, such as common configuration files. However, many developers making many changes to the same file at the same time is a recipe for trouble.

**Note**: DevOps Insights ignores files that have these extensions:

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
