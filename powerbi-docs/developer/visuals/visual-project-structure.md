---
title: Power BI visual project structure
description: This article describes the folder and file structure of a Power BI visual project
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ""
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
---

# Power BI visual project structure

The best way to start creating a new Power BI visual is to use the Power BI visuals [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) tool.

To create a new visual, navigate to the directory you want the Power BI visual to reside in, and run the command:

`pbiviz new <visual project name>`

Running this command creates a Power BI visual folder that contains the following files:

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## Folder and file description

This section provides information for each folder and file in the directory that the Power BI visuals **pbiciz** tool creates.  

### .vscode

This folder contains the VS code project settings.

To configure your workspace, edit the `.vscode/settings.json` file.

For more information, see [User and Workspace Settings](https://code.visualstudio.com/docs/getstarted/settings)

### assets

This folder contains the `icon.png` file.

The Power BI visuals tool uses this file as the new Power BI visual icon in the Power BI visualization pane.

<!--- ![Visualization pane](./media/visualization-pane-analytics-tab.png) --->

### src

This folder contains the visual's source code.

In this folder, the Power BI visuals tool creates the following files:
* `visual.ts` - The visual's main source code.
* `settings.ts` - The code of the visual's settings. The classes in the file provide an interface for defining your [visual's properties](./objects-properties.md#properties).

### style

This folder contains the `visual.less` file, which holds the visual's styles.

### capabilities.json

This file contains the main properties and settings (or [capabilities](./capabilities.md)) for the visual. It allows the visual to declare supported features, objects, properties, and [data view mapping](./dataview-mappings.md).

### package-lock.json

This file is automatically generated for any operations where *npm* modifies either the `node_modules` tree, or the `package.json` file.

For more information about this file, see the official [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json) documentation.

### package.json

This file describes the project package. It contains information about the project such as authors, description, and project dependencies.

For more information about this file, see the official [npm-package.json](https://docs.npmjs.com/files/package.json.html) documentation.

### pbiviz.json

This file contains the visual metadata.

To view an example `pbiviz.json` file with comments describing the metadata entries, see the [metadata entries](#metadata-entries) section.

### tsconfig.json

A configuration file for [TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

This file must contain the path to **\*.ts** file where the main class of the visual is located, as specified in the `visualClassName` property in the `pbiviz.json` file.

### tslint.json

This file contains the [TSLint configuration](https://palantir.github.io/tslint/usage/configuration/).

## Metadata entries

The comments in the following code caption from the `pbiviz.json` file, describe the metadata entries.

> [!NOTE]
> * From version 3.x.x of the **pbiciz** tool,`externalJS` isn't suported.
> * For localization support, [add the Power BI locale to your visual](./localization.md).

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## Next steps

* To understand the interactions between a visual, a user, and Power BI, see [Power BI visual concept](./power-bi-visuals-concept.md).

* Start developing your own Power BI visuals from scratch, using the [step by step guide](./custom-visual-develop-tutorial.md).