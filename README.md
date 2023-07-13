# Partner Extensions

This repository is reserved for Rancher Extensions created by Rancher Partners.  Extensions were introduced with Rancher 2.7.0. 

The "Tested & Certified -- Rancher Extension" certification is part of the SUSE "Tested & Certified" product certification framework and it aims to address the growing need for a standardized, high-quality, and reliable ecosystem of Rancher Extensions that augment the capabilities of the Rancher by SUSE platform.

## Requirements

* Charts must be Helm 3 compatible.

* Chart must be in a hosted [Helm](https://helm.sh/docs/topics/chart_repository/) or Git repository that we can reference.


## Workflow

#### 1. Fork the [Partner Extensions](https://github.com/rancher/partner-charts/) repository, clone your fork, checkout the **main** branch and pull the latest changes. 
Then create a new branch off of main

#### 2. Update the `manifest.json` with your Extension metadata.

```json
{
  "extensions": {
    "kubewarden": {
      "repo": "kubewarden/ui",
      "branch": "gh-pages",
      "versions": [
        "1.0.0",
        "1.1.0"
      ]
    }
  }
}
```

#### 3. Commit your changes
```bash
git add manifest.json
git commit -m "Submitting kubewarden/ui version 1.1.0"
```

#### 4. Push your commit
```bash
git push origin <your_branch>
```

#### 5. Open a pull request on the **main** branch

Once your pull request is approved and merged, an automated workflow will sync this repository with the build assets from the supplied repository within the `manifest.json` file. When fully synced, a new release will be created and added to the [releases](https://github.com/rancher/partner-extensions/releases) section. 

## Configuration File

Required properties for `manifest.json`
| Variable | Description |
| ------------- |------------- |
| [extension key] | This name is representative of the Extension **package** name. For example, the [clock](https://github.com/rancher/ui-plugin-examples/tree/main/pkg/clock) package within the [`ui-plugin-examples`](https://github.com/rancher/ui-plugin-examples/tree/main) repository, `clock` would be the extension key.
| repo | Defines the upstream **Github** repository to pull the build assets from.
| branch | Defines which branch to pull from the upstream `repo`
| versions | An array of version strings which correspond to the Extension **package** version(s) to be synced with this repository. For example, the [clock](https://github.com/rancher/ui-plugin-examples/tree/main/charts/clock) extension package has two versions, `0.1.0` and `0.2.0` would be added.


## Examples

```json
{
  "extensions": {
    "kamaji": {
      "repo": "clastix/rancher-extension-clastix",
      "branch": "gh-pages",
      "versions": [
        "0.1.2"
      ]
    },
    "elemental": {
      "repo": "rancher/elemental-ui",
      "branch": "main",
      "versions": [
        "1.2.0",
        "1.1.0",
        "1.0.0"
      ]
    },
    "kubewarden": {
      "repo": "kubewarden/ui",
      "branch": "gh-pages",
      "versions": [
        "1.0.0",
        "1.0.1",
        "1.0.2",
        "1.0.3",
        "1.0.4",
        "1.0.5",
        "1.0.6",
        "1.1.0"
      ]
    }
  }
}
```
