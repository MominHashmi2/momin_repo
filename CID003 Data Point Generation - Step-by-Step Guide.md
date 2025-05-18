# CID003 Data Point Generation - Step-by-Step Guide

This document outlines the complete process of generating a data point for CID003 using the `cvdp_agentic_heavy_*` repository format.

---

## Step-by-Step Instructions

### **Step 1: Create Repository**

Create a new repository following the naming pattern:

```bash
cvdp_agentic_heavy_<module_name>
```

### **Step 2: Copy External Files**

Copy all external files/folders into the `external/` directory in the `main` branch. Commit and push the changes.

### **Step 3: Create Context Branch**

Create a new branch from `main`. This branch will act as the **context** and will contain the modifications to guide the LLM.

### **Step 4: Prepare Context Branch**

In this context branch:

1. **Delete the RTL module** you want the LLM to generate.
2. **Write a detailed document** describing the deleted RTL module thoroughly so that the LLM can recreate it purely from this document.

### **Step 5: Create GitHub Issue**

With the context branch in place, create a new GitHub Issue describing the problem and attach the context branch as the reference.

### **Step 6: Open Pull Request (Context)**

Create a PR to merge the context branch into the `main` branch.

### **Step 7: Create Response Branch**

Create a new branch (response branch) from `main` and do the following:

1. **Add the deleted RTL module back** into the `external/` folder.
2. Add two metadata files:

   * `external.yml`
   * `origin.yml`
3. Add harness files in the same format as used previously for Copilot submissions.

### **Step 8: Run Harness Tests**

Run the harness to ensure all functional checks pass successfully.

### **Step 9: Push Response Branch**

Push your changes. Ensure that under the **Files Changed** tab, only the following are shown:

* The added RTL module
* `external.yml` and `origin.yml`
* Harness files

### **Step 10: Merge Response PR**

Once all validations pass, merge the response branch PR.

### **Step 11: Link Issue**

Link the merged response PR back to the original GitHub Issue for traceability.

---

## Example `external.yml` Format

```yaml
external:
  2:
    reference: cvdp_agentic_heavy_axi4_lite
    context: context_cid003_dp1
```


