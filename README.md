<div align="center">
  
# JFrog Frogbot

[![Frogbot](images/frogbot-intro.png)](#readme)

[![Scanned by Frogbot](https://raw.github.com/jfrog/frogbot/master/images/frogbot-badge.svg)](https://github.com/jfrog/frogbot#readme)
[![Go Report Card](https://goreportcard.com/badge/github.com/jfrog/frogbot)](https://goreportcard.com/report/github.com/jfrog/frogbot)

| Branch |                                                                                                                                                                                    Status                                                                                                                                                                                    |
|:------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| master | [![Build status](https://github.com/jfrog/frogbot/actions/workflows/test.yml/badge.svg?branch=master)](https://github.com/jfrog/frogbot/actions/workflows/test.yml?branch=master)  [![GitHub Action Test](https://github.com/jfrog/frogbot/actions/workflows/action-test.yml/badge.svg?branch=master)](https://github.com/jfrog/frogbot/actions/workflows/action-test.yml?branch=master) |
|  dev   |                [![Build status](https://github.com/jfrog/frogbot/actions/workflows/test.yml/badge.svg?branch=dev)](https://github.com/jfrog/frogbot/actions/workflows/test.yml?branch=dev)  [![GitHub Action Test](https://github.com/jfrog/frogbot/actions/workflows/action-test.yml/badge.svg?branch=dev)](https://github.com/jfrog/frogbot/actions/workflows/action-test.yml?branch=dev)                |

</div>

<div id="what-is-frogbot"></div>

## 🤖 About JFrog Frogbot
### Overview

JFrog Frogbot is a Git bot that scans your Git repositories for security vulnerabilities.
1. It scans pull requests immediately after they are opened but before they are merged. This process notifies you if the pull request is about to introduce new vulnerabilities to your code. This unique capability ensures the code is scanned and can be fixed even before vulnerabilities are introduced into the codebase.
2. It scans the Git repository periodically and creates pull requests with fixes for detected vulnerabilities.

#### It supports the following Git providers:

| <img height="20" width="20"  src="https://cdn.simpleicons.org/GitHub" alt="GitHub" /> GitHub | <img height="20" width="20"  src="https://cdn.simpleicons.org/GitLab" alt="GitLab" />  GitLab | <img height="20" width="20"  src="https://cdn.simpleicons.org/AzureDevops" alt="Azure" />  Azure Repos | <img height="20" width="20"  src="https://cdn.simpleicons.org/Bitbucket" alt="Bitbucket" />  Bitbucket Server |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|


#### It supports the following package managers are:

|<img height="20" width="20"  src="https://cdn.simpleicons.org/Go" alt="Go" /> Go|<img height="20" width="20"  src="https://cdn.simpleicons.org/Gradle" alt="Gradle" /> Gradle|<img height="20" width="20"  src="https://cdn.simpleicons.org/ApacheMaven" alt="Maven" /> Maven|<img height="20" width="20"  src="https://cdn.simpleicons.org/npm" alt="npm" /> npm|<img height="20" width="20"  src="https://cdn.simpleicons.org/Yarn" alt="Yarn" /> Yarn|
|:----|:----|:----|:----|:----|
|<img height="20" width="20"  src="https://cdn.simpleicons.org/.NET" alt=".NET" /> .NET|<img height="20" width="20"  src="https://cdn.simpleicons.org/NuGet" alt="NuGet" /> NuGet|<img height="20" width="20"  src="https://cdn.simpleicons.org/Python" alt="Pip" /> Pip|<img height="20" width="20"  src="https://cdn.simpleicons.org/Python" alt="Pipenv" /> Pipenv|<img height="20" width="20"  src="https://cdn.simpleicons.org/Poetry" alt="Poetry" /> Poetry|


### Why use JFrog Frogbot?
- **Software Composition Analysis (SCA)**: Scan your project dependencies for security issues. For selected security issues, get leverage-enhanced CVE data from our JFrog Security Research team. Frogbot uses JFrog's vast vulnerabilities database, to which we continuously add new component vulnerability data. Also included is VulnDB, the industry's most comprehensive security database, to further extend the range of vulnerabilities detected and fixed by Frogbot.
- **Validate Dependency Licenses**: Ensure that the licenses for the project's dependencies are in compliance with a predefined list of approved licenses.
- **Static Application Security Testing (SAST)**: Provides fast and accurate security-focused engines that detect zero-day security vulnerabilities on your source code sensitive operations, while minimizing false positives.
- **CVE Vulnerability Contextual Analysis**: This feature uses the code context to eliminate false positive reports on vulnerable dependencies that are not applicable to the code. For CVE vulnerabilities that are applicable to your code, Frogbot will create pull request comments on the relevant code lines with full descriptions regarding the security issues caused by the CVE. Vulnerability Contextual Analysis is currently supported for Python, JavaScript, and Java code.
- **Secrets Detection**: Detect any secrets left exposed inside the code. to stop any accidental leak of internal tokens or credentials.
- **Infrastructure as Code scans (IaC)**: Scan Infrastructure as Code (Terraform) files for early detection of cloud and infrastructure misconfigurations.

> **_NOTE:_** **SAST**, **Vulnerability Contextual Analysis**, **Secrets Detection** and **Infrastructure as Code scans**
  > require the [JFrog Advanced Security Package](https://jfrog.com/xray/).

## 🖥️ Setting up Frogbot

Set up Frogbot on your preferred CI server:

<img height="20" width="20"  src="https://cdn.simpleicons.org/GitHubActions" alt="GitHubActions" /> [GitHub Actions](docs/install-github.md)

<img height="20" width="20"  src="https://cdn.simpleicons.org/Jenkins" alt="Jenkins" /> [Jenkins](docs/templates/jenkins/README.md)

<img height="20" width="20"  src="https://cdn.simpleicons.org/JfrogPipelines" alt="jfrogpipelines" /> [JFrog Pipelines](docs/templates/jfrog-pipelines/README.md)

<img height="20" width="20"  src="https://cdn.simpleicons.org/Gitlab" alt="Gitlab" /> [GitLab CI](docs/install-gitlab.md)

<img height="20" width="20"  src="https://cdn.simpleicons.org/AzurePipelines" alt="AzurePipelines" /> [Azure Pipelines](docs/install-azure-pipelines.md)

<details>
  <summary> Optional - set up a FREE JFrog Environment in the Cloud</summary>

Frogbot requires a JFrog environment to scan your projects. If you don't have an environment, we can set up a free environment in the cloud for you. Just run one of the following commands in your terminal to set up an environment in less than a minute.

The commands will do the following:

1. Install [JFrog CLI](https://www.jfrog.com/confluence/display/CLI/JFrog+CLI) on your machine.
2. Create a FREE JFrog environment in the cloud for you.

**For macOS and Linux, use curl**

```
curl -fL "https://getcli.jfrog.io?setup" | sh
```

**For Windows, use PowerShell**

```
powershell "Start-Process -Wait -Verb RunAs powershell '-NoProfile iwr https://releases.jfrog.io/artifactory/jfrog-cli/v2-jf/[RELEASE]/jfrog-cli-windows-amd64/jf.exe -OutFile $env:SYSTEMROOT\system32\jf.exe'" ; jf setup
```

After the setup is complete, you'll receive an email with your JFrog environment connection details, which can be stored as secrets in Git.

</details>

<details>
  <summary>Advanced - Customize advanced settings with frogbot-config.yml</summary>
    
- [Creating the frogbot-config.yml File](docs/frogbot-config.md)

</details>

<div id="reporting-issues"></div>

## 🚥 Using Frogbot

<details>
  <summary>Scanning pull requests</summary>

### General

Frogbot uses [JFrog Xray](https://jfrog.com/xray/) (version 3.29.0 and above is required) to scan your pull requests. It adds the scan results as a comment on the pull request. If no new vulnerabilities are found, Frogbot will also add a comment, confirming this.

The following features use the package manager used for building the project:
* Software Composition Analysis (SCA)
* Vulnerability Contextual Analysis

### How to use Pull Request scanning?
  <details>
    <summary>GitHub</summary>

After you create a new pull request, the maintainer of the Git repository can trigger Frogbot to scan the pull request from the pull request UI.

> **_NOTE:_** The scan output will include only new vulnerabilities added by the pull request.
> Vulnerabilities that aren't new, and existed in the code before the pull request was created, will not be included in
> the
> report. In order to include all of the vulnerabilities in the report, including older ones that weren't added by this
> PR, use the includeAllVulnerabilities parameter in the frogbot-config.yml file.

The Frogbot GitHub scan workflow is:

1. The developer opens a pull request.
2. The Frogbot workflow automatically gets triggered and a [GitHub environment](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment#creating-an-environment) named `frogbot` becomes pending for the maintainer's approval.
   ![](https://raw.githubusercontent.com/jfrog/frogbot/master/images/github-pending-deployment.png)

3. The maintainer of the repository reviews the pull request and approves the scan: [![](./images/github-deployment.gif)](#running-frogbot-on-github)
4. Frogbot can be triggered again following new commits, by repeating steps 2 and 3.

  </details>

  <details>
    <summary>GitLab</summary>

After you create a new merge request, the maintainer of the Git repository can trigger Frogbot to scan the merge request from the merge request UI.

> **_NOTE:_** The scan output will include only new vulnerabilities added by the merge request.
> Vulnerabilities that aren't new, and existed in the code before the merge request was created, will not be included in
> the
> report. In order to include all of the vulnerabilities in the report, including older ones that weren't added by this
> merge request, use the includeAllVulnerabilities parameter in the frogbot-config.yml file.

The Frogbot GitLab flow is as follows:

1. The developer opens a merge request.
2. The maintainer of the repository reviews the merge request and approves the scan by triggering the manual _frogbot-scan_ job.
3. Frogbot is then triggered by the job, it scans the merge request and adds a comment with the scan results.
4. Frogbot can be triggered again following new commits, by triggering the _frogbot-scan_ job again.
   ![](https://raw.githubusercontent.com/jfrog/frogbot/master/images/gitlab-run-button.png)

  </details>
  
  <details>
    <summary>Azure Repos</summary>

After you create a new pull request, Frogbot will automatically scan it.

> **_NOTE:_** The scan output will include only new vulnerabilities added by the pull request.
> Vulnerabilities that aren't new, and existed in the code before the pull request was created, will not be included in
> the
> report. In order to include all the vulnerabilities in the report, including older ones that weren't added by this
> PR, use the includeAllVulnerabilities parameter in the frogbot-config.yml file.

The Frogbot Azure Repos scan workflow is:

1. The developer opens a pull request.
2. Frogbot scans the pull request and adds a comment with the scan results.
3. Frogbot can be triggered again following new commits, by adding a comment with the `rescan` text.

  </details>

  <details>
    <summary>Bitbucket Server</summary>

After you create a new pull request, Frogbot will automatically scan it.

> **_NOTE:_** The scan output will include only new vulnerabilities added by the pull request.
> Vulnerabilities that aren't new, and existed in the code before the pull request was created, will not be included in
> the
> report. In order to include all of the vulnerabilities in the report, including older ones that weren't added by this
> PR, use the includeAllVulnerabilities parameter in the frogbot-config.yml file.

The Frogbot scan on Bitbucket Server workflow:

1. The developer opens a pull request.
2. Frogbot scans the pull request and adds a comment with the scan results.
3. Frogbot can be triggered again following new commits, by adding a comment with the `rescan` text.

  </details>

### 👮 Security note for pull requests scanning

When installing Frogbot using JFrog Pipelines, Jenkins, and Azure DevOps, Frogbot will not wait for a maintainer's approval before scanning newly opened pull requests. Using Frogbot with these platforms is therefore not recommended for open-source projects.

When installing Frogbot using GitHub Actions and GitLab however, Frogbot will initiate the scan only after it is approved by a maintainer of the project. The goal of this review is to ensure that external code contributors don't introduce malicious code as part of the pull request. Since this review step is enforced by Frogbot when used with GitHub Actions and GitLab, it is safe to be used for open-source projects.

### Scan results
#### Software Composition Analysis (SCA), Vulnerability Contextual Analysis and Infrastructure as Code scans (IaC)

Frogbot adds the scan results to the pull request in the following format:

##### 👍 No issues

If no new vulnerabilities are found, Frogbot automatically adds the following comment to the pull request:

[![](https://raw.githubusercontent.com/jfrog/frogbot/master/resources/v2/noVulnerabilityBannerPR.png)](#-no-issues)

##### 👎 Issues were found

If new vulnerabilities are found, Frogbot adds them as a comment on the pull request. For example:

[![](https://raw.githubusercontent.com/jfrog/frogbot/master/resources/v2/vulnerabilitiesBannerPR.png)](#-issues)

<br>

**VULNERABLE DEPENDENCIES**
|                                                      SEVERITY                                                       | CONTEXTUAL ANALYSIS                  | DIRECT DEPENDENCIES                  | IMPACTED DEPENDENCY                   | FIXED VERSIONS                       |
|:-------------------------------------------------------------------------------------------------------------------:| :----------------------------------: | :----------------------------------: | :-----------------------------------: | :---------------------------------: |
|   ![](https://raw.githubusercontent.com/jfrog/frogbot/master/resources/v2/notApplicableCritical.png)<br>Critical    | $\color{#3CB371}{\textsf{Not Applicable}}$ |minimist:1.2.5 | minimist:1.2.5 | [0.2.4]<br>[1.2.6] |
|   ![](https://raw.githubusercontent.com/jfrog/frogbot/master/resources/v2/applicableHighSeverity.png)<br>    High   | $\color{#FF7377}{\textsf{Applicable}}$ |protobufjs:6.11.2 | protobufjs:6.11.2 | [6.11.3] |
|     ![](https://raw.githubusercontent.com/jfrog/frogbot/master/resources/v2/notApplicableHigh.png)<br>    High      | $\color{#3CB371}{\textsf{Not Applicable}}$ |lodash:4.17.19 | lodash:4.17.19 | [4.17.21] |

<br>

**INFRASTRUCTURE AS CODE**
|                                                      SEVERITY                                                       | FILE           | LINE:COLUMN   | FINDING                   
|:-------------------------------------------------------------------------------------------------------------------:| :------------: | :-----------: | :-----------------------------------: 
|   ![](https://raw.githubusercontent.com/jfrog/frogbot/master/resources/v2/notApplicableCritical.png)<br>Critical    | test.js        | 1:20          | kms_key_id='' was detected
|   ![](https://raw.githubusercontent.com/jfrog/frogbot/master/resources/v2/applicableHighSeverity.png)<br>    High   | mock.js        | 4:30          | Deprecated TLS version was detected

##### Secrets Detection
When Frogbot detects secrets that have been inadvertently exposed within the code of a pull request, it promptly triggers an email notification to the user who pushed the corresponding commit. The email address utilized for this notification is sourced from the committer's Git profile configuration. Moreover, Frogbot offers the flexibility to direct the email notification to an extra email address if desired. To activate email notifications, it is necessary to configure your SMTP server details as variables within your Frogbot workflows.

![](https://raw.githubusercontent.com/jfrog/frogbot/master/images/secrets-email.png)

##### Validate Dependency Licenses
When Frogbot scans newly opened pull requests, it checks the licenses of any new direct project dependencies introduced by the pull request. If Frogbot identifies licenses that are not listed in a predefined set of approved licenses, it appends a comment to the pull request providing this information.

![](https://raw.githubusercontent.com/jfrog/frogbot/master/images/violated-licenses.png)

</details>

<details>
  <summary>Scanning repositories</summary>

### Automatic pull requests creation
Frogbot scans your Git repositories periodically and automatically creates pull requests for upgrading vulnerable dependencies to a version with a fix.

![](./images/fix-pr.png)

### Adding Security Alerts
  
For GitHub repositories, issues that are found during Frogbot's periodic scans are also added to the [Security Alerts](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/managing-code-scanning-alerts-for-your-repository) view in the UI. 
The following alert types are supported:

#### 1. CVEs on vulnerable dependencies

![](./images/github-code-scanning.png)

![](./images/github-code-scanning-content.png)

#### 2. Secrets that are exposed in the code
![](./images/github-code-scanning-secrets-content.png)

#### 3. Infrastructure as Code (Iac) issues on Terraform packages
![](./images/github-code-scanning-iac-content.png)

</details>

</details>

## 📛 Adding the Frogbot badge

You can show people that your repository is scanned by Frogbot by adding a badge to the README of your Git repository.

![](./images/frogbot-badge.svg)

You can add this badge by copying the following markdown snippet and pasting it into your repository's README.md file.
```
[![Scanned by Frogbot](https://raw.github.com/jfrog/frogbot/master/images/frogbot-badge.svg)](https://github.com/jfrog/frogbot#readme)
```

## 🔥 Reporting issues

Please help us improve Frogbot by [reporting issues](https://github.com/jfrog/frogbot/issues/new/choose) you encounter.

<div id="contributions"></div>

## 💻 Contributions

We welcome pull requests from the community. To help us improve this project, please read our [Contribution](./CONTRIBUTING.md#-guidelines) guide.
