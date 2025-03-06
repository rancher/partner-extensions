# Partner Extensions

This repository is reserved for Rancher Extensions created by Rancher Partners.  Extensions were introduced with Rancher 2.7.0. 

### What are the requirements for adding a project to this repository?

TODO: Confirm with Troy - verified partner

TODO: Confirm with Troy - how supply and track business contact (if not included below)?

Before submitting an extension to this repository, you must become a
[SUSE "Ready" Verified partner](https://www.suse.com/product-certification/ready/certify-your-applications/).
You can start this process with a [Partner Application](https://partner.suse.com/s/apply).

To certify your extension as SUSE "Ready", you need to attest that the software:

* Has been tested on RKE2 or K3s and publishes documentation showing supported versions, including
  * version of Rancher (e.g. 2.11) 
  * Rancher-supported distribution of Kubernetes (RKE2, K3s, EKS, etc.)
  * version of Kubernetes (e.g. 1.32)
* Is supported by your organization on the declared Rancher versions and configurations
* Is actively maintained and proactively updated
  * critical vulnerabilities are patched in a timely way
  * release notes disclose serious bugs and vulnerabilities
* Has a license and/or terms and conditions for use available in public documentation or via the chart itself
* Does not compete commercially with Rancher Prime

Once your extension is certified as SUSE "Ready", there are a few more requirements for inclusion in this repository. Your extension must:

* Packaged as an helm chart using the rancher extensions packaging script
* The extension helm chart needs to be available from a public github repository
* Extension must include appropriate metadata. For more information on metadata see [here](https://extensions.rancher.io/extensions/next/api/metadata). This includes but not exclusively
  * An extension icon
  * Compatibility annotations. For more information see [here](https://extensions.rancher.io/extensions/next/extensions-configuration#configurable-annotations)
* Be compatible with at least the current version of Rancher  

TODO: require description, home url, maintainers in package.json

Meeting these requirements ensures that Rancher users can easily deploy your extension.

> This repository is not intended for certain kinds of software. For example:
> * extensions that meet the needs of only a few people
> * software maintained by an open source community without any backing organization with which SUSE can have a partnership

### How do I add my extension to this repository?

All extensions must to be reviewed by Rancher before they will be published to this repository.
1. Submit your extension (see [workflow](#workflow))
2. Rancher will review your extension (see [Extension Review](#extension-review)) and will either
  a. Approve
  b. Approve with advisories
     - There are recommendations that will not block inclusion in the repo
  c. Request Changes
     - There are required changed that must be completed before including in repo
   > In order to conduct the review Rancher may need to reach out to you for a test environment or demonstration of your extension 
3. Upon approval Rancher will merge the PR which will begin the automation required to include your repo.
  - The extension will then be available to applicable Rancher's when their chart repo refresh

## Workflow

#### 1. Fork the [Partner Extensions](https://github.com/rancher/partner-extensions/) repository, clone your fork, checkout the **main** branch and pull the latest changes. 
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

For more information see Appendix [Manifest File](#manifest-file) section

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

## Extension Review

- Understand scope and functionality
- Impact on security, scaling and performance
- Code Review
- UX Review
- Documentation and test approach TODO: Confirm, do we include these?

## Appendix

### Manifest File

Required properties for `manifest.json`
| Variable | Description |
| ------------- |------------- |
| [extension key] | This name is representative of the Extension **package** name. For example, the [clock](https://github.com/rancher/ui-plugin-examples/tree/main/pkg/clock) package within the [`ui-plugin-examples`](https://github.com/rancher/ui-plugin-examples/tree/main) repository, `clock` would be the extension key.
| repo | Defines the upstream **Github** repository to pull the build assets from.
| branch | Defines which branch to pull from the upstream `repo`
| versions | An array of version strings which correspond to the Extension **package** version(s) to be synced with this repository. For example, the [clock](https://github.com/rancher/ui-plugin-examples/tree/main/charts/clock) extension package has two versions, `0.1.0` and `0.2.0` would be added.

#### Examples

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



