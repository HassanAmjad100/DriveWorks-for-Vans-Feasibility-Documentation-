# SolidWorks API vs DriveWorks – Feasibility & Integration Options

## Purpose

To compare SolidWorks API and DriveWorks as potential tools for automating the transition from our van configurator (frontend) to CAD-based manufacturing-ready models.

---

## 1. SolidWorks API – Overview

SolidWorks provides a powerful COM-based API that allows developers to automate nearly every part of the SolidWorks workflow.

### Key Capabilities

* Open and edit existing part/assembly files
* Modify dimensions and features based on input
* Suppress/unsuppress features conditionally
* Export drawings (e.g., DXF, STEP, STL)
* Add custom properties and metadata

### Requirements

* SolidWorks Professional or Premium license
* Programming in VB.NET, C#, or C++
* Local machine with SolidWorks installed

### Use Case for Big Bear Vans

* Build a **parametric master CAD model**
* Write macros/scripts that read JSON from our configurator
* Automatically update dimensions or layout
* Export manufacturing files

### Pros

* Fully customizable and powerful
* No need to purchase additional software if already licensed
* Fine control over model behavior and file export

### Cons

* Requires a developer with SolidWorks + coding experience
* Complex for teams without strong CAD API knowledge
* Difficult to scale web automation without server-side workstations

---

## 2. DriveWorks – Overview

DriveWorks is an automation platform that works on top of SolidWorks. It lets users create rules-driven models and forms for CAD automation.

### Versions & Features

| Version          | Cost Estimate | Features                                       |
| ---------------- | ------------- | ---------------------------------------------- |
| DriveWorksXpress | Free          | Basic form + rules, works within SolidWorks UI |
| DriveWorks Solo  | \~\$2,000     | Form builder, rules engine, model automation   |
| DriveWorks Pro   | \$10K–\$20K+  | Web configurator, full team workflows          |

### Use Case for Big Bear Vans

* Start with DriveWorksXpress or Solo
* Build a form that mirrors our current configurator logic
* Link form inputs to rules inside SolidWorks
* Regenerate parts/assemblies based on selections

### Pros

* No code needed — visual rule builder
* Built for engineers, not developers
* Easier to maintain than raw API macros
* Good documentation and tutorials

### Cons

* Costs increase with more automation
* Web integration requires DriveWorks Pro (expensive)
* Locked into the DriveWorks ecosystem

---

## 3. Comparison Table

| Feature              | SolidWorks API       | DriveWorks (Solo/Xpress)         |
| -------------------- | -------------------- | -------------------------------- |
| Coding required      | Yes (C#, VB.NET)     | No (drag-and-drop forms + rules) |
| Setup complexity     | High                 | Low to medium                    |
| Frontend integration | Possible via backend | Only with Pro version            |
| Customization        | Very high            | Medium to high                   |
| Cost                 | Free (if licensed)   | Paid (Solo), Free (Xpress)       |
| Best for             | Developers           | Engineers/Non-devs               |
| Works offline        | Yes                  | Yes                              |
| Ideal team size      | Medium to large      | Small teams                      |

---

## 4. Recommendation

For Big Bear Vans, We recommend the following approach:

### Short-Term

* Stick with manual engineering based on JSON exported from frontend
* Begin building parametric master models in SolidWorks
* Test small macros (SolidWorks API) for internal automation

### Medium-Term

* Evaluate DriveWorks Solo to reduce engineer workload
* Use rule-driven modeling to generate production files

### Long-Term (Scaling Stage)

* Consider DriveWorks Pro if the business scales and web-to-production automation becomes critical

---

## 5. Next Steps

* Test exporting config data from frontend
* Ask CAD engineer to prepare parametric base model
* Create and test a basic SolidWorks macro that changes model based on JSON
* Install DriveWorksXpress (free) and explore basic rules setup
* Estimate cost/value of DriveWorks Solo if needed
