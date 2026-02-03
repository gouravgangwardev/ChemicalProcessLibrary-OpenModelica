# ChemicalProcessLibrary

A modular, equation-based chemical process simulation library developed in **OpenModelica**, focused on reusable reactor modeling and extensible reaction kinetics.  
This library is submitted as part of the **FOSSEE Semester Long Internship 2026 – Screening Task 2 (Chemical Process Simulation Library Development in OpenModelica)**.

---

## Overview

This repository presents a structured and reusable **chemical process simulation library** built using **equation-based modeling principles** in Modelica.  
The primary objective is to demonstrate **library-oriented design**, **modularity**, and **chemical engineering fundamentals** through reactor and reaction models.

The library supports:
- Multiple reactor types (CSTR, Batch Reactor)
- Multiple reaction kinetics (irreversible and reversible first-order)
- Clear separation between **interfaces**, **reactors**, **reactions**, **properties**, and **examples**
- Easy extensibility for future models

All models strictly use **SI units** (`Modelica.Units.SI`) and avoid hard-coded numerical values inside equations.

---

## Library Structure

ChemicalProcessLibrary/
│
├── Interfaces/
│   ├── MaterialPort.mo
│   └── Feed.mo
│
├── Reactors/
│   ├── BaseReactor.mo
│   ├── CSTR.mo
│   └── BatchReactor.mo
│
├── Reactions/
│   ├── ReactionBase.mo
│   ├── FirstOrderReaction.mo
│   └── ReversibleFirstOrderReaction.mo
│
├── Properties/
│   └── IdealLiquidDensity.mo
│
├── Examples/
│   ├── CSTR_SteadyState.mo
│   ├── CSTR_ParametricStudy.mo
│   ├── CSTR_Comparison.mo
│   └── BatchReactor_Dynamic.mo
│
└── README.md



---

## Modeling Philosophy

- **Equation-based modeling only** (no procedural code)
- **Modularity by design**
- **Replaceable reaction models** enable switching kinetics without modifying reactor code
- **Partial base classes** enforce consistency and reusability
- **Clear separation of concerns** (reactors ≠ reactions ≠ properties)

---

## Screening Task Mapping

### ✅ Step 1 — Steady-State CSTR (Mandatory)
- Implemented in `Reactors/CSTR.mo`
- Demonstrated in `Examples/CSTR_SteadyState.mo`
- Outputs:
  - Outlet concentration of A
  - Conversion of A

### ✅ Step 2 — Library-Oriented Reactor Design (Mandatory)
- `BaseReactor.mo` implemented as a **partial model**
- Reaction kinetics implemented as **replaceable models**
- Reactor models are reusable and extensible

### ⭐ Step 3 — Property & Kinetics Extension (Optional)
- Ideal liquid density model included in `Properties/IdealLiquidDensity.mo`
- Reversible first-order kinetics included
- Comparative and parametric studies provided

---

## Examples Description

| Example | Description |
|------|------------|
| **CSTR_SteadyState** | Steady-state CSTR performance and outlet concentration |
| **BatchReactor_Dynamic** | Dynamic behavior: concentration and conversion vs time |
| **CSTR_ParametricStudy** | Sensitivity to reactor volume and feed concentration |
| **CSTR_Comparison** | Comparison of irreversible vs reversible kinetics under identical conditions |

Each example simulates successfully in OpenModelica and produces meaningful plots for validation.

---

## How to Run

1. Install **OpenModelica (latest official release recommended)**
2. Open OMEdit
3. Load the project directory or individual `.mo` files
4. Navigate to the `Examples` folder
5. Simulate any example model

No external simulators or proprietary tools are used.

---

## Extensibility

The library is designed to be easily extended:
- Add new reactors by extending `BaseReactor`
- Add new kinetics by extending `ReactionBase`
- Add physical property models (temperature, density, energy balances)
- Enable advanced studies such as optimization or control

---

## Limitations

- Single-component reaction system
- Isothermal operation
- Constant density (except where property model is used)
- No energy balances (can be added as an extension)

---

## License

This work is intended for **academic and open-source use** as part of the FOSSEE initiative.

---

## Author

Developed by **Gourav Gangwar**  
FOSSEE Semester Long Internship 2026 – Screening Submission

