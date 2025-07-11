# Structured JSON Export – Configurator to CAD Bridge

## Purpose

This document outlines the need for and implementation plan of a structured JSON export system from the current React-based van configurator. The goal is to generate a machine-readable configuration file alongside the `.glb` scene export for CAD engineers to use during manual, semi-automated, or fully automated model creation in SolidWorks.

---

## Problem

The current system exports a `.glb` file of the visual scene using Three.js's `GLTFExporter`. This file is uploaded to S3 and passed to the backend. However, it does not include any structured metadata about the user’s configuration choices.

### Limitations of Current Approach

* `.glb` is binary and not easily readable by CAD engineers
* No record of user-selected layout, materials, components, or preferences
* Engineers must interpret visuals manually, increasing time and error risk

---

## Solution

Introduce a structured configuration export in the form of a `van-config.json` file. This JSON will be uploaded alongside the `.glb` and contain all user selections made during the configuration process.

Later, this structured JSON can be used to:

* Populate a **Google Sheet** that mirrors a SolidWorks **Design Table**
* Feed directly into SolidWorks macros or API-based scripts

---

## Example JSON Schema (Draft)

```json
{
  "configName": "Default",
  "layout": "Calavera",
  "roofHeight": "High",
  "cabinetMaterial": "Walnut Matte",
  "electrical": {
    "battery": "300Ah",
    "solar": "400W"
  },
  "features": ["Shower", "Roof Deck"],
  "color": "Fog Grey",
  "dimensions": {
    "length": 1000,
    "height": 400,
    "thickness": 20
  }
}
```

This structure can easily be mapped to the SolidWorks Design Table once the engineer shares the variable names.

---

## Frontend Implementation Plan

### 1. Capture Configuration

Within `MultiStepForm.jsx`, track all user-selected options (layout, dimensions, materials, etc.) into a single config object.

### 2. Export JSON Function

```js
const exportConfigAsJSON = (configObject) => {
  const blob = new Blob([JSON.stringify(configObject, null, 2)], {
    type: 'application/json'
  });
  return new File([blob], 'van-config.json');
};
```

### 3. Upload to S3

Use the same S3 upload logic already implemented for `.glb` files. Upload the config JSON file and store the returned S3 URL.

### 4. Send Both Files to Backend

Update the backend payload to include:

```json
{
  "name": "Hassan Amjad",
  "email": "hasan@example.com",
  "phone": "1234567890",
  "modelUrl": "https://s3.amazonaws.com/van-models/xyz.glb",
  "configUrl": "https://s3.amazonaws.com/van-configs/xyz.json"
}
```

---

## Developer Notes

* Keep the config schema aligned with the future **Google Sheet headers** that the CAD engineer will use in their Design Table
* Once the final variable mapping is shared, use the config to directly populate a compatible `.csv` or Google Sheet row
* Consider adding internal `version`, `userID`, or `timestamp` fields for traceability

---

## Benefits

* Engineers get a readable configuration file
* Can support **manual entry**, **copy-paste to Excel**, or **future macro/API scripts**
* Enables better handoff from frontend to engineering
* Serves as structured documentation for customer selections

---

## Optional Future Enhancements

* Auto-embed config JSON inside `.glb` as metadata (Three.js supports this)
* Allow users to download `.json` directly as a record
* Validate config data before export using a defined schema
* Add export history and version control on backend

---

