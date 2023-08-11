---
title: Scan for vulnerabilities and misconfigurations of your OVHcloud Managed Kubernetes with Trivy
excerpt: Find out how to scan for vulnerabilities and misconfigurations of your OVHcloud Managed Kubernetes with Trivy
updated: 2022-06-01
---

**Last updated 1st June 2022**

<style>
 pre {
     font-size: 14px;
 }
 pre.console {
   background-color: #300A24; 
   color: #ccc;
   font-family: monospace;
   padding: 5px;
   margin-bottom: 5px;
 }
 pre.console code {
   b   font-family: monospace !important;
   font-size: 0.75em;
   color: #ccc;
 }
 .small {
     font-size: 0.75em;
 }
</style>

## Objective

[Trivy](https://github.com/aquasecurity/trivy) is a tool that scans for vulnerabilities, secrets and misconfigurations for containers and other artifacts.

![Trivy](images/trivy-logo.png)

Trivy detects vulnerabilities in:

- container images
- filesystems
- Git repositories (a GitHub action exists)
- Kubernetes clusters
- Terraform and CloudFormation Infrastructure as Code (IaC) files
- ...

Trivy also scans hardcoded secrets like passwords, API keys and tokens.

![Trivy](images/trivy-overview.png)

More than a simple Docker container image, Trivy can now scan a wide range of different data like Kubernetes clusters.

For your information, Trivy is a read-only tool, it only retrieves informations in order to help you to secure and sanitize your cluster. It does not modify or delete resources on a Kubernetes cluster.

Read more about [Trivy here](https://aquasecurity.github.io/trivy/v0.28.1/docs/).

At OVHcloud, we like to provide you with the best products and services. For us, security is important, that's why we want to help you discover Trivy which will help you secure your OVHcloud Managed Kubernetes with helpful reports.

In this guide you will:

- Install Trivy CLI
- Generate and export reports
- Install the Trivy Kubernetes Operator

You can use the *Reset cluster* function in the Public Cloud section of the [OVHcloud Control Panel](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com.au/&ovhSubsidiary=au){.external} to reinitialize your cluster before following this tutorial.

## Requirements

This tutorial presupposes that you already have a working OVHcloud Managed Kubernetes cluster, and some basic knowledge of how to operate it.

Moreover, follow the [deploying a Hello World application](/pages/public_cloud/containers_orchestration/managed_kubernetes/deploying-an-application) documentation in order to have an example application running on your cluster.

At this time you should have a running Kubernetes cluster with hello-world deployment and pod like below:

<pre class="console"><code>$ kubectl get po,deploy
NAME                                          READY   STATUS    RESTARTS   AGE
pod/hello-world-deployment-559d658ffb-q5t7j   1/1     Running   0          35m

NAME                                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/hello-world-deployment   1/1     1            1           35m
</code></pre>

## Instructions

### Installing Trivy CLI

You can [install Trivy](https://aquasecurity.github.io/trivy/latest/getting-started/installation/) on your computer from the binaries, the source, HomeBrew, Arch Linux, Ubuntu, etc. and even use it directly from a Docker image.

For this tutorial you will install it via HomeBrew:

```bash
brew install aquasecurity/trivy/trivy
```

The output should be like this:

<pre class="console"><code>$ brew install aquasecurity/trivy/trivy
Running `brew update --preinstall`...
==> Auto-updated Homebrew!
Updated 2 taps (homebrew/core and homebrew/cask).
==> New Formulae
dtrx                                     glider                                   hatch                                    terramate                                yorkie
==> Updated Formulae
Updated 326 formulae.
==> New Casks
bili-downloader                                    roam-research                                      rustdesk                                           swiftcord
==> Updated Casks
Updated 194 casks.
==> Deleted Casks
crystax-ndk

==> Tapping aquasecurity/trivy
Cloning into '/opt/homebrew/Library/Taps/aquasecurity/homebrew-trivy'...
remote: Enumerating objects: 285, done.
remote: Counting objects: 100% (174/174), done.
remote: Compressing objects: 100% (64/64), done.
remote: Total 285 (delta 57), reused 158 (delta 52), pack-reused 111
Receiving objects: 100% (285/285), 40.87 KiB | 747.00 KiB/s, done.
Resolving deltas: 100% (92/92), done.
Tapped 1 formula (12 files, 54.2KB).
==> Downloading https://github.com/aquasecurity/trivy/releases/download/v0.28.1/trivy_0.28.1_macOS-ARM64.tar.gz
==> Downloading from https://objects.githubusercontent.com/github-production-release-asset-2e65be/180687624/f79fc5e4-30f4-461f-be69-598e11d7b81d?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJY
######################################################################## 100.0%
==> Installing trivy from aquasecurity/trivy
Warning: A newer Command Line Tools release is available.
Update them from Software Update in System Preferences or run:
  softwareupdate --all --install --force

If that doesn't show you any updates, run:
  sudo rm -rf /Library/Developer/CommandLineTools
  sudo xcode-select --install

Alternatively, manually download them from:
  https://developer.apple.com/download/all/.
You should download the Command Line Tools for Xcode 13.3.

🍺  /opt/homebrew/Cellar/trivy/0.28.1: 5 files, 76.1MB, built in 1 second
==> Running `brew cleanup trivy`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
</code></pre>

After the installation, check that the `trivy` CLI is working correctly:

```bash
trivy version
```

You should have a behavior like this:

<pre class="console"><code>$ trivy version
Version: 0.28.1
</code></pre>

Trivy is correctly installed on your computer, you can now use it to scan your Kubernetes cluster and display a report with existing vulnerabilities and misconfigurations.

### Generate Trivy reports

The `trivy` CLI contains several commands and subcommands, here is an extract:

```
COMMANDS:
   image, i          scan an image
   filesystem, fs    scan local filesystem for language-specific dependencies and config files
   rootfs            scan rootfs
   repository, repo  scan remote repository
   server, s         server mode
   config, conf      scan config files
   plugin, p         manage plugins
   kubernetes, k8s   scan kubernetes vulnerabilities and misconfigurations
   sbom              generate SBOM for an artifact
   version           print the version
   help, h           Shows a list of commands or help for one command
```

As you can see, the `trivy` CLI contains a lot of commands and options, as you can scan vulnerabilities in container images, file systemes, Git repositories, configuration issues, etc. For this tutorial we will focus on the `k8s` command.

When you execute `trivy k8s`, the command works like the `kubectl` command. So when you execute the CLI, it searches your Kubernetes cluster configuration.

First, you will ask Trivy to generate a summary report only on the `default` namespace.

To generate this report, simply execute the CLI:

```bash
trivy k8s -n default --report summary
```

This command runs tests on all nodes in the `default` namespace and displays a summary report:

<pre class="console"><code>$ trivy k8s -n default --report summary
5 / 5 [--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 2 p/s

Summary Report for kubernetes-admin@my-cilium-cluster
┌───────────┬───────────────────────────────────┬────────────────────┬───────────────────┬───────────────────┐
│ Namespace │             Resource              │  Vulnerabilities   │ Misconfigurations │      Secrets      │
│           │                                   ├───┬───┬────┬───┬───┼───┬───┬───┬───┬───┼───┬───┬───┬───┬───┤
│           │                                   │ C │ H │ M  │ L │ U │ C │ H │ M │ L │ U │ C │ H │ M │ L │ U │
├───────────┼───────────────────────────────────┼───┼───┼────┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
│ default   │ Deployment/hello-world-deployment │ 5 │ 9 │ 18 │ 2 │   │   │   │ 3 │ 8 │   │   │   │   │   │   │
└───────────┴───────────────────────────────────┴───┴───┴────┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
Severities: C=CRITICAL H=HIGH M=MEDIUM L=LOW U=UNKNOWN
</code></pre>

As you can see, in our `default` namespace, our OVHcloud Managed Kubernetes cluster (and with an "hello world" application deployed) has several vulnerabilities and misconfigurations.

We will take a closer look at theses vulnerabilities and misconfigurations. For that, you will ask Trivy to generate a full report, still in the `default` namespace.

To generate this full report, simply execute the CLI:

```bash
trivy k8s -n default --report all
```

You should obtain a report and a list of vulnerabilities and misconfigurations like this:

<pre class="console"><code>$ trivy k8s -n default --report all
5 / 5 [--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 2 p/s

ovhplatform/hello (alpine 3.8.1)

Total: 34 (UNKNOWN: 0, LOW: 2, MEDIUM: 18, HIGH: 9, CRITICAL: 5)

┌───────────────┬────────────────┬──────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────────────┐
│    Library    │ Vulnerability  │ Severity │ Installed Version │ Fixed Version │                            Title                             │
├───────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ libbz2        │ CVE-2019-12900 │ CRITICAL │ 1.0.6-r6          │ 1.0.6-r7      │ bzip2: out-of-bounds write in function BZ2_decompress        │
│               │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-12900                   │
├───────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ libcrypto1.0  │ CVE-2018-0734  │ MEDIUM   │ 1.0.2p-r0         │ 1.0.2q-r0     │ openssl: timing side channel attack in the DSA signature     │
│               │                │          │                   │               │ algorithm                                                    │
│               │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2018-0734                    │
│               ├────────────────┤          │                   │               ├──────────────────────────────────────────────────────────────┤
│               │ CVE-2018-5407  │          │                   │               │ openssl: Side-channel vulnerability on SMT/Hyper-Threading   │
│               │                │          │                   │               │ architectures (PortSmash)                                    │
│               │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2018-5407                    │
├───────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ libcrypto1.0  │ CVE-2019-1547  │ MEDIUM   │ 1.0.2p-r0         │ 1.0.2t-r0     │ openssl: side-channel weak encryption vulnerability          │
│               │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1547                    │
├───────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ libcrypto1.0  │ CVE-2019-1551  │ MEDIUM   │ 1.0.2p-r0         │ 1.0.2u-r0     │ openssl: Integer overflow in RSAZ modular exponentiation on  │
│               │                │          │                   │               │ x86_64                                                       │
│               │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-1551                    │
├───────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
...
musl          │ CVE-2019-14697 │ CRITICAL │ 1.1.19-r10        │ 1.1.19-r11    │ musl libc through 1.1.23 has an x87 floating-point stack     │
│               │                │          │                   │               │ adjustment im ......                                         │
│               │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2019-14697                   │
├───────────────┤                │          │                   │               │                                                              │
│ musl-utils    │                │          │                   │               │                                                              │
│               │                │          │                   │               │                                                              │
│               │                │          │                   │               │                                                              │
└───────────────┴────────────────┴──────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────────────┘

default-Deployment-hello-world-deployment-2137444644.yaml (kubernetes)

Tests: 31 (SUCCESSES: 20, FAILURES: 11, EXCEPTIONS: 0)
Failures: 11 (UNKNOWN: 0, LOW: 8, MEDIUM: 3, HIGH: 0, CRITICAL: 0)

MEDIUM: Container 'hello-world' of Deployment 'hello-world-deployment' should set 'securityContext.allowPrivilegeEscalation' to false
════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════
A program inside the container can elevate its own privileges and run as root, which might give the program control over the container and node.

See https://avd.aquasec.com/misconfig/ksv001
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 default-Deployment-hello-world-deployment-2137444644.yaml:120-128
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 120 ┌                 - image: ovhplatform/hello
 121 │                   imagePullPolicy: Always
 122 │                   name: hello-world
 123 │                   ports:
 124 │                     - containerPort: 80
 125 │                       protocol: TCP
 126 │                   resources: {}
 127 │                   terminationMessagePath: /dev/termination-log
 128 └                   terminationMessagePolicy: File
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
...
LOW: Container 'hello-world' of Deployment 'hello-world-deployment' should set 'securityContext.runAsGroup' > 10000
════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════
Force the container to run with group ID > 10000 to avoid conflicts with the host’s user table.

See https://avd.aquasec.com/misconfig/ksv021
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 default-Deployment-hello-world-deployment-2137444644.yaml:120-128
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 120 ┌                 - image: ovhplatform/hello
 121 │                   imagePullPolicy: Always
 122 │                   name: hello-world
 123 │                   ports:
 124 │                     - containerPort: 80
 125 │                       protocol: TCP
 126 │                   resources: {}
 127 │                   terminationMessagePath: /dev/termination-log
 128 └                   terminationMessagePolicy: File
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
</code></pre>


The report can be very big. So, in order to take a look at our vulnerabilities and misconfigurations in a new report, you can also display only URGENT vulnerabilities:

<pre class="console"><code>$ trivy k8s -n default --report all --severity MEDIUM,HIGH,CRITICAL
5 / 5 [--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 3 p/s

ovhplatform/hello (alpine 3.8.1)

Total: 32 (MEDIUM: 18, HIGH: 9, CRITICAL: 5)

...


default-Deployment-hello-world-deployment-2908255124.yaml (kubernetes)

Tests: 20 (SUCCESSES: 17, FAILURES: 3, EXCEPTIONS: 0)
Failures: 3 (MEDIUM: 3, HIGH: 0, CRITICAL: 0)

MEDIUM: Container 'hello-world' of Deployment 'hello-world-deployment' should set 'securityContext.allowPrivilegeEscalation' to false
════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════
A program inside the container can elevate its own privileges and run as root, which might give the program control over the container and node.

See https://avd.aquasec.com/misconfig/ksv001
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 default-Deployment-hello-world-deployment-2908255124.yaml:120-128
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 120 ┌                 - image: ovhplatform/hello
 121 │                   imagePullPolicy: Always
 122 │                   name: hello-world
 123 │                   ports:
 124 │                     - containerPort: 80
 125 │                       protocol: TCP
 126 │                   resources: {}
 127 │                   terminationMessagePath: /dev/termination-log
 128 └                   terminationMessagePolicy: File
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────


MEDIUM: Container 'hello-world' of Deployment 'hello-world-deployment' should set 'securityContext.runAsNonRoot' to true
════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════════
'runAsNonRoot' forces the running image to run as a non-root user to ensure least privileges.

See https://avd.aquasec.com/misconfig/ksv012
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 default-Deployment-hello-world-deployment-2908255124.yaml:120-128
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 120 ┌                 - image: ovhplatform/hello
 121 │                   imagePullPolicy: Always
 122 │                   name: hello-world
 123 │                   ports:
 124 │                     - containerPort: 80
 125 │                       protocol: TCP
 126 │                   resources: {}
 127 │                   terminationMessagePath: /dev/termination-log
 128 └                   terminationMessagePolicy: File
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
...
</code></pre>

And, finally, for this part, you can also scan only a specific resource, only a specific deployment for example:

```
trivy k8s -n default --report summary deployment/hello-world-deployment
```

You should obtain a result like this:

<pre class="console"><code>$ trivy k8s -n default --report summary deployment/hello-world-deployment
1 / 1 [--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 1 p/s

Summary Report for kubernetes-admin@my-cilium-cluster
┌───────────┬───────────────────────────────────┬────────────────────┬───────────────────┬───────────────────┐
│ Namespace │             Resource              │  Vulnerabilities   │ Misconfigurations │      Secrets      │
│           │                                   ├───┬───┬────┬───┬───┼───┬───┬───┬───┬───┼───┬───┬───┬───┬───┤
│           │                                   │ C │ H │ M  │ L │ U │ C │ H │ M │ L │ U │ C │ H │ M │ L │ U │
├───────────┼───────────────────────────────────┼───┼───┼────┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
│ default   │ Deployment/hello-world-deployment │ 5 │ 9 │ 18 │ 2 │   │   │   │ 3 │ 8 │   │   │   │   │   │   │
└───────────┴───────────────────────────────────┴───┴───┴────┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
Severities: C=CRITICAL H=HIGH M=MEDIUM L=LOW U=UNKNOWN
</code></pre>

### Export reports locally

You can generate and save a report, for all your namespaces, with the `-o` command

```bash
$ trivy k8s -n default --report summary -o trivy-report.txt
```

This will save the report in your working directory:

<pre class="console"><code>$ trivy k8s -n default --report summary -o trivy-report.txt

1 / 5 [------------------------------------>__________________________________________________________________________________________________________________________________________________] 20.00% ? p/s5 / 5 [--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------] 100.00% 2 p/s

$ ll trivy-report.txt
-rw-r--r--  1 aurelievache  staff   1,8K 30 mai 17:00 trivy-report.txt
</code></pre>

### Installing Trivy Kubernetes Operator

Trivy can also be run as a native Kubernetes Operator, which is designed to be used in CI/CD pipelines.

This Kubernetes Operator continuously scans your Kubernetes cluster for security issues, and generates security reports as Kubernetes Custom Resources. It watches Kubernetes for state changes and automatically triggers scans in response to changes, for example initiating a vulnerability scan when a new Pod is created.

For this tutorial we are using the [Trivy Helm chart](https://github.com/aquasecurity/trivy/tree/main/helm/trivy).

Add the Trivy Helm repository:

```bash
helm repo add aqua https://aquasecurity.github.io/helm-charts/
helm repo update
```

These commands will add the Trivy Helm repository to your local Helm chart repository and update the installed chart repositories:

<pre class="console"><code>$ helm repo add aqua https://aquasecurity.github.io/helm-charts/
helm repo update
"aqua" has been added to your repositories
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "aqua" chart repository
Update Complete. ⎈Happy Helming!⎈
</code></pre>

Install the latest version of Trivy with `helm install` command:

```bash
helm install trivy-operator aqua/trivy-operator \
   --namespace trivy-system \
   --create-namespace \
   --set="trivy.ignoreUnfixed=true" \
   --version v0.0.3
```

This command will install the latest version of the Trivy Kubernetes Operator, create a new `trivy-system` namespace and configure it to scan all namespaces, except kube-system and trivy-system:

<pre class="console"><code>$ helm install trivy-operator aqua/trivy-operator \
   --namespace trivy-system \
   --create-namespace \
   --set="trivy.ignoreUnfixed=true" \
   --version v0.0.3
NAME: trivy-operator
LAST DEPLOYED: Tue May 31 09:07:04 2022
NAMESPACE: trivy-system
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
You have installed Trivy Operator in the trivy-system namespace.
It is configured to discover Kubernetes workloads and resources in
all namespace(s).

Inspect created VulnerabilityReports by:

    kubectl get vulnerabilityreports --all-namespaces -o wide

Inspect created ConfigAuditReports by:

    kubectl get configauditreports --all-namespaces -o wide

Inspect created CISKubeBenchReports by:

    kubectl get ciskubebenchreports -o wide

Inspect the work log of trivy-operator by:

    kubectl logs -n trivy-system deployment/trivy-operator
</code></pre>

You can check if the Trivy pod is correctly running:

<pre class="console"><code>$ kubectl get po -n trivy-system
NAME                              READY   STATUS    RESTARTS   AGE
trivy-operator-7bdc55f8d6-h6kvp   1/1     Running   0          49s
</code></pre>

Now you can inspect `VulnerabilityReports` for all your namespaces, with the following command:

```
kubectl get vulnerabilityreports --all-namespaces -o wide
```

You should obtain a result like this:

<pre class="console"><code>$ kubectl get vulnerabilityreports --all-namespaces -o wide
NAMESPACE   NAME                                                       REPOSITORY          TAG      SCANNER   AGE   CRITICAL   HIGH   MEDIUM   LOW   UNKNOWN
default     replicaset-hello-world-deployment-559d658ffb-hello-world   ovhplatform/hello   latest   Trivy     58s   5          9      18       2     0
</code></pre>

You can check your deployments for several critical, high, medium and low vulnerabilities.

The Kubernetes operator also generates `ConfigAuditReports`:

```
kubectl get configauditreports --all-namespaces -o wide
```

You should obtain a result like this:

<pre class="console"><code>$ kubectl get vuln --all-namespaces -o wide
NAMESPACE   NAME                                                       REPOSITORY          TAG      SCANNER   AGE   CRITICAL   HIGH   MEDIUM   LOW   UNKNOWN
default     replicaset-hello-world-deployment-559d658ffb-hello-world   ovhplatform/hello   latest   Trivy     13m   5          9      18       2     0
</code></pre>

Thanks to the Kubernetes Operator, it's possible to integrate Trivy into your CI/CD pipeline to check cluster vulnerabilities and misconfiguration issues.
It thus allows you to automate a way to access reports, export the metrics from the vulnerability reports into Prometheus, add dashboards into Grafana, set up alerting, etc.

## Go further

- If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/en-au/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

- Join our community of users on <https://community.ovh.com/en/>.
