

##  Research : Exploring SolidWorks API & DriveWorks

---

###  1. **SolidWorks API Overview**

**What is it?**
SolidWorks provides a COM-based API that allows you to **programmatically create, open, edit, and export CAD files**.

* Language: Primarily **VB.NET**, **C#**, and **C++**
* Access: You need a **SolidWorks Professional or Premium license**
* Use Case: You write a macro or external program that can:

  * Open a “master” model
  * Change dimensions/materials/features
  * Save it as DXF, STL, STEP, etc.

**Key Capabilities**:

| Action                     | Feasibility | Notes                              |
| -------------------------- | ----------- | ---------------------------------- |
| Open & edit a part file    | Yes         | Possible with API                  |
| Modify dimensions          | Yes         | Must be parametric                 |
| Export manufacturing files | Yes         | Easily automated                   |
| Create parts from scratch  | No          | Complex, not recommended initially |

**Documentation**:
SolidWorks API docs: [https://help.solidworks.com/](https://help.solidworks.com/)

---

### 2. **DriveWorks Overview**

**What is it?**
DriveWorks is a design automation platform that works *on top of* SolidWorks. Think of it like a no-code/low-code version of what you’d do with the API.

**DriveWorks has 3 tiers**:

| Version          | Cost                | Features                                                          |
| ---------------- | ------------------- | ----------------------------------------------------------------- |
| DriveWorksXpress | Free                | Very limited, part of every SolidWorks license                    |
| DriveWorks Solo  | \$\$ (\~\$2K)       | Local automation, form-driven configs, rule logic                 |
| DriveWorks Pro   | \$\$\$ (\~\$10–20K) | Full web-based configurators, team workflows, advanced automation |

**What DriveWorks Can Do**:

* Build forms like your multi-step configurator
* Attach rules and logic to control model behavior
* Update SolidWorks models and generate outputs automatically
* Even connect to **databases, emails, or ERP systems** (in Pro)

---

###  API vs DriveWorks – Quick Comparison

| Feature                               | SolidWorks API                      | DriveWorks                   |
| ------------------------------------- | ----------------------------------- | ---------------------------- |
| Code required                         | Yes (VB.NET/C#)                     | No (GUI + rule logic)        |
| Best for                              | Developers                          | Engineers/non-coders         |
| Suitable for team of interns?         | Medium — needs 1 developer          |  Easier to manage            |
| Output control (DXF, PDF, etc.)       | Yes                                 | Yes                          |
| Integrates with frontend configurator | Yes (custom build needed)           | Pro version only (expensive) |
| Cost                                  | No extra cost (but dev time needed) | Paid licenses (Solo/Pro)     |

---

## Challenges to Expect

* SolidWorks must be installed on the **same system** that runs the API or DriveWorks.
* You can't run SolidWorks in the cloud easily (licensing restrictions).
* DriveWorks Pro for web automation is **expensive**.
* Building a fully custom solution from API is **developer-heavy** and will require **deep CAD knowledge** to modify models via code.

---

##  Final Recommendation (Realistic & Scalable)

* **Short-term**: Export config from frontend → engineer manually updates parametric CAD model
* **Mid-term**: Use SolidWorks macro or API to apply config automatically to a master model
* **Long-term**: Adopt DriveWorks Solo (affordable) if build volume increases and team grows

---


