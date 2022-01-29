# Module Management+
Module Management+ is packed with features and design imporvements designed to make manageing large module list easy. MM+ provides more detailed information about modules at a glance and allows you to read packages changelogs/readmes directly in foundry meant to help you find answers quickly.

Some of the notable features of Module Management+ is the Addition of new tags such as readme, changelog, issues and authors. A cleaner easier list view of the modules with stripped rows and more spacing to make the viewing experiance easier on the eyes. The ability to see conflicts and known issues with your installed modules

## I am a developer, how do I register my module with MM+?
Well you don't technically register anything with MM+. MM+ was designed to auto detect supported details and display them to the user. It tries to implement many of the features from the [Package Manifest+](https://foundryvtt.wiki/en/development/manifest-plus) Guidelines right into Foundry. 

If you want your modules Readme or Changelog to show up in MM+ all you have to do is provide your `README.md` and/or `CHANGELOG.md` files with your module, MM+ will scan Foundry's modules and auto detect and display this information.

## What about Conflicts and Known Issues?
This is where [Package Manifest+](https://foundryvtt.wiki/en/development/manifest-plus) Guidelines come in.
> Please note, though I attempted to follow the guidelines provided by Package Manifest+, I do not follow them word for word, MM+ is very flexible

## Registering a Conflict
To register a conflict in MM+ all you have to do use use the `conflicts` keyword in your `module.json` file. This is an array of conflicts.

| Field | Required | Description |
|-------|----------|-------------|
| name  | true    | If you do not provide a conflicting module name, MM+ will register the conflict as a known issue |
| description | false | This is the text that will be displayed to the user about the conflict/known issue. If not description is defined, the module will list **No Details Provided** |
| versionMin | false | The conflict/known issue will only be shown if the version number is greater or equal to the version listed here |
| versionMax | false | The conflict/known issue will only be shown if the version number is less than the number listed here |
```json
"conflicts": [
	{
		"name": "module-name",
		"description": "A description detailing the conflict between the two modules.",
		"versionMin": "a.b.c",
		"versionMax": "a.b.c"
	}
]
```

## Registering a Known Issue
To register a known issue in MM+ all you have to do use use the `issues` keyword in your `module.json` file. This is an array of issues.
| Field | Required | Description |
|-------|----------|-------------|
| description | false | This is the text that will be displayed to the user about the conflict/known issue. If not description is defined, the module will list **No Details Provided** |
| versionMin | false | The conflict/known issue will only be shown if the version number is greater or equal to the version listed here |
| versionMax | false | The conflict/known issue will only be shown if the version number is less than the number listed here |
```json
"issues": [
	{
		"description": "A description detailing the conflict between the two modules.",
		"versionMin": "a.b.c",
		"versionMax": "a.b.c"
	}
]
```

## Wait so if I find a known issue or conflict, I have to push a module update to register it?
Nope, this is actually what the `conflicts.json` file is meant for on my github. Lets say you come across a know issue and don't have time to fix it, or you find out about a package incompatibility. Its kinda crazy to suggest that you push a whole update to you module just to update the module.json file to state that there is a conflict or known issue. So I've decided to self host a file that can be update via the community with a pull request or file an issue. 

| Field | Required | Description |
|-------|----------|-------------|
| moduleID | true | This is your modules name |
| conflictingModuleID | false | Leaving this field empty will define your conflict as a known issue. Its great for when you find out there is a major bug in your module, but you may not be able to fix it ASAP |
| description | false | This is the text that will be displayed to the user about the conflict/known issue. If not description is defined, the module will list **No Details Provided** |
| versionMin | true | The conflict/known issue will only be shown if the version number is greater or equal to the version listed here |
| versionMax | false | The conflict/known issue will only be shown if the version number is less than the number listed here |

An example of defining a conflict would look like this:
```json
[
	{
		"moduleID": "module-name",
		"conflictingModuleID": "conflicting-module-name",
		"description": "A description detailing the conflict between the two modules.",
		"versionMin": "a.b.c",
		"versionMax": "a.b.c"
	}
]
```
An example of defining a known issue would look like this:
```json
[
	{
		"moduleID": "module-name",
		"description": "A description detailing the conflict between the two modules.",
		"versionMin": "a.b.c"
	}
]
```

## Supported Modules
### Package Manifest+
Module Management+ uses the [Package Manifest+](https://foundryvtt.wiki/en/development/manifest-plus) Schema as a guideline for defining conflicts, deprecated modules, and additional author information. I did my best to match support and the intended usecase of the Package Manifest+ Schema, if you notice something is missing or conflicting, plese let me know.

### Bug Reporter
Module Management+ adds support for [🐛 Bug Reporter](https://foundryvtt.com/packages/bug-reporter). If Bug Reporter is enabled and the module has opt'ed into the system, you can click that icon to quickly report an issue with that module using `Bug Reporter`. If you don't have bug reporter, don't worry the issues link will still appear in the modules tags.

## Credits
Libraries used in creating Module Management+
- [Marked.js](https://github.com/markedjs/marked) 
- [DOMPurify](https://github.com/cure53/DOMPurify) 
- [Popper.js](https://popper.js.org/) 
- [Tippy.js](https://atomiks.github.io/tippyjs/) 
