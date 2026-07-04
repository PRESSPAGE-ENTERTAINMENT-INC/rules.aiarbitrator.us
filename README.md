# **📘 AI Arbitrator Rulebooks (Public Repository)**  
This repository contains the **deterministic rulebooks** used by the PPE **AI Arbitrator** at **aiarbitrator.us** to render small‑claims arbitration decisions governed by:

- **Federal Arbitration Act (FAA)**  
- **FAA §7 subpoena authority**  
- **State small‑claims statutes**  
- **County‑level venue and procedural rules**

All rulebooks in this repository are **public**, version‑controlled, and automatically consumed by the ONNX‑based deterministic arbitrator engine.

---

# **🏛️ Purpose of This Repository**
The AI Arbitrator is designed to produce **deterministic**, **auditable**, and **reproducible** decisions in small‑claims matters.  
This repository provides:

- A **transparent rulebook hierarchy**  
- A **public change history** for attorney review  
- A **stable reference** for CLE training and certification  
- A **machine‑readable structure** for the arbitrator engine  

Every rulebook update is committed with:

- Attorney name  
- Bar number  
- Change log  
- Git commit history (public)

This ensures **no clerk or system operator can modify rulebooks**, preserving procedural integrity.

---

# **📁 Repository Structure**

```
rulebooks/
   faa/
      faa.json
      subpoena.json
      intake.json
   states/
      FL/
         state.json
         counties/
            alachua.json
            miami_dade.json
      MD/
         state.json
         counties/
            montgomery.json
            prince_georges.json
      TX/
         state.json
         counties/
            harris.json
            travis.json
```

## **Hierarchy Explanation**

### **1. FAA Layer (`faa/`)**
Contains national‑level rules:

- FAA §7 subpoena constraints  
- Hearing‑attendance requirements  
- Deterministic subpoena issuance logic  
- Award confirmation & vacatur rules  
- Intake rules applicable nationwide  

Your uploaded document confirms that **most federal circuits prohibit pre‑hearing discovery subpoenas**, requiring witness attendance at a hearing before arbitrators (“Section 7 requires the attendance of a witness…”).  
These constraints are encoded in `subpoena.json`.  


---

### **2. State Layer (`states/<STATE>/state.json`)**
Defines:

- Small‑claims case types  
- Dollar limits  
- Eligibility & exclusions  
- State‑specific procedural rules  
- Pre‑suit requirements (e.g., demand letters)

Small‑claims case types are **defined by the state**, not counties.

---

### **3. County Layer (`states/<STATE>/counties/<COUNTY>.json`)**
Defines:

- Venue boundaries  
- Filing fees  
- Local forms  
- County‑specific procedural variations  

Counties **administer** small‑claims procedures but do **not** define case types.

---

# **⚙️ Deterministic Rulebook Loading Order**
The ONNX arbitrator loads rulebooks in this strict order:

1. **FAA**  
2. **State**  
3. **County**  
4. **Forum rules (internal)**

This ensures:

- FAA §7 compliance  
- State‑accurate case‑type eligibility  
- County‑accurate venue & fees  
- Fully deterministic outcomes  

---

# **📜 Rulebook Format**
All rulebooks follow a strict JSON schema:

- `metadata` (version, jurisdiction, last updated)  
- `definitions` (terms used by the arbitrator)  
- `rules` (deterministic decision logic)  
- `procedures` (filing, hearing, subpoena, award)  
- `limits` (dollar caps, case‑type eligibility)  
- `citations` (statutory references)

Each file is validated before acceptance.

---

# **🔐 Governance & Change Requests**
Only licensed attorneys may submit rulebook change requests.

Each request must include:

- Attorney name  
- Bar number  
- Description of change  
- Reason / authority  
- Digital signature  
- JSON patch or diff

Clerks may **view** and **submit**, but **cannot edit**.

All changes are committed publicly.

---

# **🎓 CLE Accreditation**
This repository supports the Amerione Corporation CLE program:

**“Deterministic AI Arbitration Under the FAA:  
A Procedural Framework for Subpoena Enforcement and Award Confirmation.”**

Attorneys learn:

- Deterministic AI vs. generative AI  
- FAA §7 subpoena limitations  
- State/county small‑claims structures  
- How rulebooks drive arbitrator decisions  
- How to submit rulebook corrections  

---

# **📨 Subpoena Logic (FAA §7)**  
Under **FAA §7**, subpoena authority belongs **exclusively to the arbitrator**.  
Because the PPE **AI Arbitrator Forum does not use oral arguments or live testimony**, all evidence, testimony, and arguments must be submitted **in writing**.  
The subpoena rules therefore adapt FAA §7’s hearing‑attendance requirement into a **written‑hearing model**.

## **Federal Baseline (FAA §7)**  
- **Only the arbitrator may issue third‑party subpoenas**  
- Subpoenas may compel **written testimony** submitted for the hearing  
- Subpoenas may compel **documents**, but only **as part of written testimony**  
- Federal circuits generally **prohibit pre‑hearing discovery subpoenas**  
- Discovery‑style production is allowed **only by party agreement**  
- The “hearing” requirement of §7 is satisfied through a **written evidentiary hearing**, not an oral one  

Your uploaded document confirms:

> “Section 7 requires the attendance of a witness at a hearing…”  
> “Pre‑hearing discovery subpoenas are not permitted in most federal circuits.”

In this forum, “attendance” is satisfied by **timely written submission** to the arbitrator.

---

# **📝 Written‑Only Hearing Model (Forum Rule)**  
Because this forum is **paper‑only**, the following rules apply:

- All testimony is **written testimony**  
- All arguments are **written arguments**  
- All exhibits are **document submissions**  
- No oral hearings, no live witnesses, no cross‑examination  
- The arbitrator conducts a **written evidentiary hearing** by reviewing all submitted materials  
- Subpoenas compel **written compliance**, not physical appearance  

This preserves:

- FAA §7 compliance  
- Deterministic decision‑making  
- Zero subjectivity  
- Full reproducibility  
- No credibility assessments based on demeanor  

---

# **📍 State Variations (Notably New York)**  
While FAA §7 limits subpoena issuance to arbitrators, some states expand this authority:

- **New York (C.P.L.R. § 7505)**  
  - Arbitrator **and** attorney of record may issue subpoenas  
  - Subpoenas may compel written testimony and documents  
  - NYSE/NASD rules also allow attorney‑issued subpoenas  

All other states follow the FAA/RUAA/UAA model:

- **Arbitrator‑only subpoena authority**  
- Written‑only compliance in this forum  

---

## **📁 Repository Encoding**  
This logic is encoded in:

- **`faa/subpoena.json`**  
  - `issuer = ["arbitrator"]`  
  - `mode = "written_only"`  
  - `hearing = "written_evidentiary_hearing"`  

- **`states/NY/state.json`**  
  - `issuer = ["arbitrator", "attorney_of_record"]`  
  - `mode = "written_only"`  

This ensures the AI Arbitrator applies the correct subpoena‑issuer rules and the correct **written‑hearing model** for every jurisdiction.

---

# **🌐 Public Access**
All rulebooks are publicly accessible at:

**[https://rules.aiarbitrator.us](https://rules.aiarbitrator.us)**

This ensures:

- Transparency  
- Public auditability  
- Attorney training  
- Deterministic reproducibility  

---

# **📄 License**
This repository is released under the **MIT License** to ensure maximum public accessibility and academic use.

---

# **🤝 Contributions**
Attorney contributions are welcome through:

- Pull requests  
- Issue submissions  
- Rulebook change requests (CLE participants)

All contributions must follow the deterministic rulebook schema.
