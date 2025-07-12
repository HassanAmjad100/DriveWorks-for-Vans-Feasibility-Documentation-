# Final Research Summary – CAD Automation for Big Bear Vans

## Overview

This document wraps up the 3-day research sprint focused on connecting our web-based van configurator to the SolidWorks-based CAD engineering workflow. The goal was to explore feasible options to reduce manual work for the engineering team while keeping the solution realistic for a small team.

---

##  What We Started With

* A React + Three.js frontend that exports `.glb` files
* Engineers manually rebuild van components in SolidWorks based on visual `.glb`s
* No structured config export or automation between sales → CAD

---

## What We Built and Documented

### 1. `README.md` – Feasibility Overview

* Defined the current bottleneck in handing off configuration data to engineers
* Proposed a lean, phased plan using structured JSON and optional CAD automation

### 2. `solidworks-driveworks-analysis.md`

* Compared SolidWorks API and DriveWorks tools
* Explained why DriveWorks Pro is overkill and not cost-efficient for now
* Identified macros and the native SolidWorks API as scalable alternatives

### 3. `config-export-implementation.md`

* Designed a structured `van-config.json` schema
* Described frontend tasks to capture and export config data
* Provided working logic for exporting and uploading alongside `.glb`

### 4. `cad-handoff-workflow.md`

* Mapped how exported JSON + `.glb` are used by engineers
* Documented manual, macro, and API-assisted SolidWorks update paths
* Included placeholder for CAD variable mapping (from engineer)

### 5. `design-table-workflow.md`

* Detailed how our engineer uses Excel-based SolidWorks Design Tables
* Proposed a Google Sheet structure to match expected CAD inputs
* Showed how the exported JSON can convert to Sheet rows

### 6. `resources.md`

* Collected all tutorials, docs, videos, and examples used during research

---



## Final Recommendations

###  Immediate Plan (Now)

* Export structured JSON from frontend → save to S3
* Engineer manually enters dimensions in Excel Design Table
* Sync frontend schema with sheet column headers once engineer shares them

### Mid-Term Plan (Next 1–2 Months)

* Write a SolidWorks macro that reads config JSON and auto-updates dimensions
* Auto-generate variants in SolidWorks without needing full DriveWorks

### Long-Term (Scaling Stage)

* Evaluate DriveWorks Solo or full DriveWorks Pro only if:

  * Build volume increases significantly
  * Non-technical team needs access to parametric generation from browser

---

##  Reference

* [Loom walkthrough video](https://www.loom.com/share/0c283be2893542dc9f4dd5ffefbef1aa?source=embed_watch_on_loom_cta)
* Screenshots of SolidWorks Design Table integration and PMS task

---

##  Deliverables Submitted to GitHub



* `README.md`
* `config-export-implementation.md`
* `cad-handoff-workflow.md`
* `design-table-workflow.md`
* `solidworks-driveworks-analysis.md`
* `resources.md`

---

##  Final Message

This documentation fully closes the research sprint. It lays the foundation for both low-effort manual CAD support and longer-term automation using SolidWorks’ built-in tools.

No new platforms are required — just structured coordination between the frontend and engineering based on a shared config format.

This path is scalable, realistic, and future-ready.

---

End of Research – 12 July 2025
