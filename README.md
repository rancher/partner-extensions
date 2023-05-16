# Partner Extensions

This repository is reserved for Rancher Extensions created by Rancher Partners.  Extensions were introduced with Rancher 2.7.0. 

The "Tested & Certified -- Rancher Extension" certification is part of the SUSE "Tested & Certified" product certification framework and it aims to address the growing need for a standardized, high-quality, and reliable ecosystem of Rancher Extensions that augment the capabilities of the Rancher by SUSE platform.

## Requirements

* Charts must be Helm 3 compatible.
    

* Chart must be in a hosted [Helm](https://helm.sh/docs/topics/chart_repository/) or Git repository that we can reference.


## Workflow

#### 1. Fork the [Partner Extensions](https://github.com/rancher/partner-charts/) repository, clone your fork, checkout the **main** branch and pull the latest changes. 
Then create a new branch off of main

#### 2. Create subdirectories in `packages` in the form of `<vendor>/<chart>`
```bash
cd partner-charts
mkdir -p packages/suse/kubewarden-controller

```
#### 3. Create your [upstream.yaml](#configuration-file) in `packages/<vendor>/<chart>`

The tool reads a configuration yaml, `upstream.yaml`, to know where to fetch the upstream chart. This file is also able to define any alterations for valid variables in the Chart.yaml as described by [Helm](https://helm.sh/docs/topics/charts/#the-chartyaml-file).

Some [example upstream.yaml](#examples) are provided below
```bash
cat <<EOF > packages/suse/kubewarden-controller/upstream.yaml
HelmRepo: https://charts.kubewarden.io
HelmChart: kubewarden-controller
Vendor: SUSE
DisplayName: Kubewarden Controller
ChartMetadata:  
  icon: https://www.kubewarden.io/images/icon-kubewarden.svg
EOF
```
#### 4. Commit your packages directory
```bash
git add packages/suse/kubewarden-controller
git commit -m "Submitting suse/kubewarden-controller"
```
#### 6. Test your configuration
1. In Rancher UI > Extensions > Kebab menu (3 dot) > Manage repositories, add your github repository
2. Go to Hamburger menu > Extensions and your extension should be listed under "Available." Install the extension
#### 7. Push your commit
```bash
git push origin <your_branch>
```
#### 8. Open a pull request to **main** branch

## Configuration File

Options for `upstream.yaml`
| Variable | Requires | Description |
| ------------- | ------------- |------------- |
| AutoInstall | | Allows setting a required additional chart to deploy prior to current chart, such as a dedicated CRDs chart
| ChartMetadata | | Allows setting/overriding the value of any valid [Chart.yaml variable](https://helm.sh/docs/topics/charts/#the-chartyaml-file)
| DisplayName | | Sets the name the chart will be listed under in the Rancher UI
| Experimental | | Adds the 'experimental' annotation which adds a flag on the UI entry
| Fetch | HelmChart, HelmRepo | Selects set of charts to pull from upstream.<br />- **latest** will pull only the latest chart version *default*<br />- **newer** will pull all newer versions than currently stored<br />- **all** will pull all versions
| GitBranch | GitRepo | Defines which branch to pull from the upstream GitRepo
| GitHubRelease | GitRepo | If true, will pull latest GitHub release from repo. Requires GitHub URL
| GitRepo | | Defines the git repo to pull from
| GitSubdirectory | GitRepo | Allows selection of a subdirectory of the upstream git repo to pull the chart from
| HelmChart | HelmRepo | Defines which chart to pull from the upstream Helm repo
| HelmRepo | HelmChart | Defines the upstream Helm repo to pull from
| Hidden | | Adds the 'hidden' annotation which hides the chart from the Rancher UI
| Namespace | | Addes the 'namespace' annotation which hard-codes a deployment namespace for the chart
| PackageVersion | | Used to generate new patch version of chart
| ReleaseName | | Sets the value of the release-name Rancher annotation. Defaults to the chart name
| TrackVersions | HelmChart, HelmRepo | Allows selection of multiple *Major.Minor* versions to track from upstream independently.
| Vendor | | Sets the vendor name providing the chart

## Examples
### Helm Repo
#### Minimal Requirements
```yaml
HelmRepo: https://charts.kubewarden.io
HelmChart: kubewarden-controller
Vendor: SUSE
DisplayName: Kubewarden Controller
```

### Git Repo
```yaml
GitRepo: https://github.com/kubewarden/helm-charts.git
GitBranch: main
GitSubdirectory: charts/kubewarden-controller
Vendor: SUSE
DisplayName: Kubewarden Controller
ChartMetadata:
  kubeVersion: '>=1.21-0'
  icon: https://www.kubewarden.io/images/icon-kubewarden.svg
```

### GitHub Release
```yaml
GitRepo: https://github.com/kubewarden/helm-charts.git
GitHubRelease: true
GitSubdirectory: charts/kubewarden-controller
Vendor: SUSE
DisplayName: Kubewarden Controller
ChartMetadata:
  kubeVersion: '>=1.21-0'
  icon: https://www.kubewarden.io/images/icon-kubewarden.svg
```
