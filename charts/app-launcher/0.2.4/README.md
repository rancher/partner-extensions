# Rancher App Launcher Extension

Rancher App Launcher Extension is a simple yet powerful tool for improved accessibility and resource discovery within Kubernetes. The extension is designed to extract ingresses from various clusters and consolidate them into a unified global resource page. With neatly organized cards for each discovered service, the tool offers an efficient method of displaying and accessing your Rancher services, making the Rancher experience seamless for both new and experienced users.

The extension intends to improve the discoverability of services and offer a straightforward way to navigate the complexities of multi-cluster environments.

<img src="./docs/images/preview.png" width="50%" alt="App Launcher Extension preview image">

## Features

- Unified resource page for all discovered services and ingresses
- Convenient access to services with a simple click
- Global apps section for user-selected favorites and global apps defined by cluster YAML files
- Grid and list views for easy navigation
- Multi-cluster support for viewing services across different clusters

## Usage

### Filter by Name

- Use the Filter box in the toolbar to search through all of the objects that your user credentials have access to across clusters.

### Filter by Cluster

- This page showcases cards for each discovered service and ingress, allowing you to conveniently open the service with a simple click.
    *The extension is designed to improve discoverability and offer a straightforward way to navigate the complexities of multi-cluster environments.*

### Change views

- The view can be changed with the view buttons in the toolbar, to switch between grid view and list view.

### Select favorites (user)

- Star service or ingress objects to surface them to the Global Apps section for easier discovery on repeat visits.
- Note: This is currently limited 

### Tag "Global" Apps (admin)

Global apps will show at the top of the App Launcher page as a combination of global apps defined by cluster YAML files and user-selected favorites.

- Apps tagged in Yaml will persist for all users.
- (currently) User-selected favorites will only persist for the user who selected them and are stored in the browser's local storage.

To select a Service or Ingress as a Global App, add the following annotation to the Service or Ingress:

```yaml
metadata:
  annotations:
    extensions.applauncher/global-app: "true"
```

## Installation

Please follow the instructions for installing the extension collection at the repository root: https://github.com/krumIO/krum-rancher-extensions/

## Development

1. Clone this repository to your machine.
2. Install the npm dependencies using the command `yarn install`.
3. Run the extension collection locally with the command `API=<Rancher Backend URL> yarn dev`.

## Contribution

Your contribution matters! If you're looking to enhance the functionalities of this extension or have innovative ideas to improve the discoverability further, we warmly welcome pull requests. Let's make the Rancher environment more user-friendly together!

## Support

If you encounter any issues, have questions or suggestions, please file them in our issue tracker. We're committed to providing a smooth user experience and appreciate your feedback to continually improve.

Rancher App Launcher Extension is here to address the need for effective discoverability within the Rancher platform. Let's make resource navigation simpler and more efficient!
