# SolidWorks Design Table Workflow – CAD Integration Without DriveWorks

## Objective

This document explains our current CAD automation path using **SolidWorks Design Tables** and why it is a better fit for our team right now compared to DriveWorks or full SolidWorks API integration. It outlines how we can structure our frontend configurator data to feed into a Google Sheet that directly maps to SolidWorks variables, enabling semi-automated model generation.

---

## 1. Why We’re Not Using DriveWorks

###  DriveWorks is not a good fit *at this stage* because:

* It requires **separate licenses** (Solo/Pro) which are **expensive**
* DriveWorks Pro (the web-enabled version) would be **overkill** for a small team
* It requires onboarding and rule setup within a separate GUI, which creates **dependency on a new toolchain**
* Our engineer is already using a more native and simpler method: **SolidWorks Design Tables**, which is part of SolidWorks Premium (already in use)

**Instead**, we focus on a lean and practical pipeline that fits our current resources.

---

## 2. Current Engineering Setup (Design Table Workflow)

### What our Mechanical Engineer is doing:

* Uses **SolidWorks Design Tables**, an internal Excel-based parametric configuration tool
* Each variable (e.g., `D1@Sketch1`, `D2@Sketch1`) controls part dimensions or features
* Each **row in the Excel table** represents a specific configuration of the van component
* The engineer manually updates or imports dimensions via Excel to regenerate parts

This is developer- and engineer-friendly and supports easy prototyping and testing.

### Example Table Structure (from screenshots):

| Config Name | D1\@Sketch1 | D2\@Sketch1 | D3\@Sketch1 | ... |
| ----------- | ----------- | ----------- | ----------- | --- |
| Default     | 500         | 300         | 100         |     |
| 1000x400    | 1000        | 400         | 100         |     |
| 1500x800    | 1500        | 800         | 100         |     |

These parameters control sketches, extrusions, fillets, and other SolidWorks features.

---

## 3. Our Role as Frontend Developers

###  How We Can Help the Engineer:

* Export user config from frontend (React) as structured **JSON or CSV**
* Match our config fields to the engineer’s design table columns (once he shares the final variable names)
* Provide a **Google Sheet or CSV template** with prefilled values
* Possibly create a script to auto-fill the design table from exported frontend data

---

## 4. Proposed Google Sheet Structure (Draft)

This will evolve once the engineer shares the actual variable names.

| Config Name | Length | Height | Thickness | Material | AddOn: Roof Deck | Battery (Ah) | Solar (W) |
| ----------- | ------ | ------ | --------- | -------- | ---------------- | ------------ | --------- |
| Default     | 500    | 300    | 15        | Walnut   | Yes              | 300          | 400       |
| Custom1     | 1000   | 400    | 20        | Maple    | No               | 200          | 200       |

### Data Types:

* `Length`, `Height`, `Thickness`, `Battery`, `Solar`: **Number (mm or watts)**
* `Material`, `Config Name`: **Text**
* `Roof Deck`: **Boolean (Yes/No)**

---

## 5. Is SolidWorks API Needed?

###  Not immediately.

Right now, the engineer works entirely inside SolidWorks using the Excel table interface. Introducing the full API would:

* Require deep SolidWorks API expertise (VB.NET, C#)
* Require running scripts on a local SolidWorks-installed machine
* Require parametric model prep and error handling code

###  But we can explore this *later* to automate the pipeline:

#### SolidWorks API Can:

* Load a part file
* Read in a JSON or Excel table
* Change dimension parameters
* Save the updated model as DXF, STEP, STL, etc.

### Future Automation Steps:

1. Engineer finalizes parametric model + variable names
2. Backend reads exported config JSON
3. API script (C#/Python w/ COM interop) injects values into the SolidWorks file
4. SolidWorks runs headless or semi-automated to export deliverables

We can start building this later if the manual process becomes repetitive.

---

## 6. Final Summary: Why This Design Table Method Works Best (Now)

| Option         | Pros                              | Cons                            |
| -------------- | --------------------------------- | ------------------------------- |
| Design Table   | Simple, no licensing, works today | Needs engineer to manage sheet  |
| SolidWorks API | Powerful, future automation ready | Requires code, setup, and time  |
| DriveWorks     | Full no-code automation           | Expensive, not needed right now |

---

## 7. Next Steps

* Engineer will share finalized parametric variable names
* We would have to create a **Google Sheet template** with matching headers
* Add logic in React app to export structured config matching those fields

---

This approach will keeps the things lean, realistic, and fully aligned with what our engineer is already doing, without overbuilding.

