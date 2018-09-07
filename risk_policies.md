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

# Creating policies and rules
{: #policies_and_rules}

Policies are sets of rules that control the gates in your delivery pipeline. If your code does not meet or exceed a policy that is enacted at a particular gate, the deployment is halted to prevent risky changes from being released.

You define policies in {{site.data.keyword.DRA_short}}. Policies are created in the {{site.data.keyword.Bluemix_notm}} organization (org) that contains {{site.data.keyword.DRA_short}}. Any applications that are in the same org can use the policy. 

## Creating policies
{: #create_policies}

To create a policy:

1. From the {{site.data.keyword.DRA_short}} navigation menu, click **Policies**.

2. Click **Create Policy** and then type a name and description for the new policy.

4. Click **Create Rule**.

4. Add at least one rule to the policy:
  1. Select the rule type.
  2. Enter details and conditions for the rule.
  3. Click **Save**.

5. When you're finished adding rules to the policy, click **Save**.

## Creating rules
{: #creating_rules}

Rules define the criteria that your policies use to judge success or failure. You might create an "Unit Testing and Test Coverage" policy that contains a unit test rule that requires 80 percent unit test success and a test coverage rule that requires 100 percent code coverage. If you add a gate that refers to this rule in a pipeline, the gate prevents any builds that don't satisfy both of the rules from proceeding. 

You can require success no matter what by marking tests as critical. To create a rule, select a policy and then click **Create Rule**. 

### Creating functional verification test rules
{: #criteria_fvt}

1. Type a description and select a format.

2. Specify the percentage of test cases that must pass to be declared successful.

3. Define any test cases that are critical. To determine test case names, see [Test result formats and tools](#criteria_formats).

4. To monitor for test case regressions, select the **Monitor for test case regression** check box.

5. Click **Save**.


### Creating unit test rules
{: #criteria_ut}

1. Type a description and select a format.

2. Specify the percentage of test cases that must pass to be declared successful.

3. Define any test cases that are critical. To determine test case names, see [Test result formats and tools](#criteria_formats).

4. To monitor for test case regressions, select the **Monitor for test case regression** check box.

5. Click **Save**.


### Creating code coverage rules
{: #criteria_codecoverage}

1. Type a description and select a format.

2. Specify the percentage of code coverage that is required to be declared successful.

3. To monitor for code coverage regressions, select the **Monitor for test case regression** check box.

4. Click **Save**.

### Creating static security scan rules
{: #criteria_static}

You can integrate {{site.data.keyword.DRA_short}} with IBM Application Security on Cloud to run static-code and dynamic-app scans. For more information about Application Security on Cloud, see [the official documentation](/docs/services/ApplicationSecurityonCloud/index.html).

1. Type a description.

2. Specify the maximum numbers of high-, medium-, and low-severity issues that are allowed by the rule. 

3. Click **Save**.

### Creating dynamic security scan rules
{: #criteria_dynamic}

You can integrate {{site.data.keyword.DRA_short}} with {{site.data.keyword.appseccloudfull}} to run dynamic-app scans. For more information about Application Security on Cloud, see [the official documentation](/docs/services/ApplicationSecurityonCloud/index.html).

1. Type a description.

2. Specify the maximum numbers of high-, medium-, and low-severity issues that are allowed by the rule. 

3. Click **Save**.

## Test result formats and tools
{: #criteria_formats}

For test results, {{site.data.keyword.DRA_short}} supports these types of metrics and formats:

* Functional Verification Test (Mocha, xUnit)
* Unit Test (Mocha, xUnit, Karma/Mocha)
* Code Coverage (Cobertura, lcov, Istanbul as json-summary report format, Blanket.js)

{{site.data.keyword.DRA_short}} also supports Selenium and Jasmine tests. These tests must be included within the officially supported tools, such as xUnit and Mocha. To learn more about using {{site.data.keyword.deliverypipeline}}, {{site.data.keyword.DRA_short}} and Selenium together, see [Running Selenium tests from the command line on a delivery pipeline](https://developer.ibm.com/devops-services/2016/07/21/running-selenium-tests-command-line-delivery-pipeline/).

For items that have test cases, you can specify critical test cases, which are tests that must pass regardless of the acceptable percentage. Critical test-case names must match the `full title` attribute of the test case.    
* For Karma/Mocha tests, the `describe()` and `it()` description strings are linked together with spaces.
* For xUnit tests, the package name, class name, and function name are linked together with spaces. This is illustrated in the following example:
  ```
  <testsuites package="test">
    <testsuite package="otc-api" name="PUT Service Instances - Test Setup" tests="2" failures="0" errors="0">
      <testcase name="#1 Authorization passed for mock user: idsb3t1@us.ibm.com"/>
      <testcase name="#2 Authorization passed for mock user: idsb3t4@us.ibm.com"/>
    </testsuite>
  </testsuite>
  ```
  That example produces these test-case names:
  ```
  test otc-api PUT Service Instances - Test Setup #1 Authorization passed for mock user: idsb3t1@us.ibm.com
  test otc-api PUT Service Instances - Test Setup #2 Authorization passed for mock user: idsb3t1@us.ibm.com
  ```

You can use Sauce Labs with {{site.data.keyword.DRA_short}} by adding the Sauce Labs tool integration to your pipeline. Then, incorporate the `SAUCE_USERNAME` and `SAUCE_ACCESS_KEY` environment variables into Selenium tests as credentials.

You can see the full titles of all of the tests in the logs after a run.  

**Notes:**
* {{site.data.keyword.DRA_short}} does not support critical tests that contain a hyphen in the full title.    
