# Helm

**Helm** is a package manager for `Kubernetes`. Just like `npm` for `node.js` or `pip` for `python`. Helm makes installing, upgrading, and managing your apps on Kubernetes much easier.

## **Problems without Helm (just Kubernetes):**

1. Defining, managing, and executing multiple manifest files.
2. Deployment ordering challenges. (e.g., MySQL first and then Springboot app second)
3. Versioning and Rollbacks for all resources.
4. Environment-specific configurations (e.g., dev, staging, production)

## **Main benefits:**

1. Reuse templates
2. Easy configuration (via values.yaml)
3. Easier upgrades/rollbacks
4. Share charts with others

## **Components of Helm**

1. Chart.yaml - Basic info about the chart: name, version, etc.
2. values.yaml - 	Default values the templates will use
3. templates/ - Main folder: contains all the YAML templates.
4. charts/ - Sub-charts/Dependencies (other charts)
5. templates/_helpers.tpl	- Optional file to define reusable template helpers (functions)

## **Helm Chart Lifecycle:**

### Create a new chart - Creates the full chart directory structure.

```bash
helm create mychart
```

### Package your chart - Creates a .tgz package that can be uploaded to a chart repository.
```bash
helm package mychart
```

### Install the chart - Installs the chart into your Kubernetes cluster. Creates a Release called myrelease. Each release of a specific chart get a revision number (starts from 1, 2,...).
```bash
helm install myrelease ./mychart
```

### List installed releases
```bash
helm list
```

### Upgrade the chart - Apply changes after you modify your chart. The revision number is assigned to the next number after the previous release's revision number.
```bash
helm upgrade myrelease ./mychart
```

### Rollback to a previous version - Roll back to revision 1 from revision 2 of the release.
```bash
helm rollback myrelease 1
```

### Uninstall (delete) the release - Deletes the release but can keep history if you want.
```bash
helm uninstall myrelease
```
