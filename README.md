# doc

**A Formal Documentation Engine for Lean 4.**

`doc` is an integrated documentation and typesetting library for Lean 4. It allows researchers and engineers to generate publication-quality LaTeX papers, books, and technical reports directly from verified Lean source code.

By leveraging Lean's metaprogramming capabilities, `doc` ensures that your documentation is never out of sync with your proofs.

---

## 🚀 Key Features

- **Intrinsic Documentation**: Use the `@[doc]` attribute to mark theorems and definitions for export.
- **Verified Typesetting**: Automatically convert Lean expressions and types into formatted LaTeX.
- **Academic Ready**: Built-in templates for **arXiv**, journals, and theses.
- **Graphic Integration**: Generate TikZ/PGFPlots diagrams directly from Lean data structures.
- **Seamless Workflow**: Integrated with `lake` for a one-command PDF generation process.

---

## 🛠 Installation

Add `doc` to your `lakefile.lean`:

```lean
require doc from git
  "[https://github.com/4137314/doc.git](https://github.com/4137314/doc.git)" @ "main"
```

Then run:
```bash
lake update
```

---

## 📖 Usage

### 1. Mark your code
Tag the declarations you want to include in your paper:

```lean
import Doc

/-- The Square of a sum identity. -/
@[doc]
theorem square_sum (a b : ℝ) : (a + b)^2 = a^2 + 2*a*b + b^2 := by
  sorry
```

### 2. Generate the Paper
Run the documentation engine via Lake:

```bash
lake run doc
```

This command will:
1. Scan your environment for `@[doc]` attributes.
2. Extract docstrings and type signatures.
3. Emit a `.tex` file.
4. Compile the `.tex` file into a `.pdf` (requires `pdflatex` or `lualatex` installed).

---

## 🏗 Roadmap (MVP)

The project is organized into three main functional domains (EPICs):

### **SRC-CORE (Introspection)**
- [ ] `SRC-CORE-ATTR`: Custom attribute registry.
- [ ] `SRC-CORE-SCAN`: Environment scraping and filtering.
- [ ] `SRC-CORE-FMT`: Pretty-printing Lean expressions for LaTeX.

### **SRC-TEX (Typesetting)**
- [ ] `SRC-TEX-PRE`: Automated LaTeX preamble generation.
- [ ] `SRC-TEX-SYM`: Unicode-to-LaTeX symbol mapping.
- [ ] `SRC-TEX-IO`: File system emission.

### **UI-CLI (Automation)**
- [ ] `UI-CLI-LAKE`: Integration with Lake scripts.
- [ ] `UI-CLI-RUN`: PDF compiler subprocess management.

---

## 🤝 Contributing

Contributions in metaprogramming, LaTeX templating, and scientific visualization are welcome.

1. Check the [Issues](https://github.com/4137314/doc/issues) for active EPICs.
2. Follow the atomic commit convention (`feat(core): ...`, `fix(tex): ...`).

---

## 📄 License

This project is licensed under the Apache 2.0 License.
