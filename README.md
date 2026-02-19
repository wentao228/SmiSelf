# SmiSelf

Official implementation of our EMNLP 2025 Main Conference paper:
**How to Make Large Language Models Generate 100% Valid Molecules?**
(The 2025 Conference on Empirical Methods in Natural Language Processing)

---

## 🧬 Overview

Molecule generation plays an important role in drug discovery and materials science, enabling the design of novel compounds with desired properties.

Large language models (LLMs) can learn many tasks from only a few examples. However, generating **valid molecules** using SMILES representations remains challenging in few-shot settings.

In this work, we investigate how to achieve **100% valid molecule generation** with LLMs:

* We evaluate SELFIES, a representation where every string corresponds to a valid molecule, but find that LLMs perform worse with SELFIES than with SMILES.
* We examine LLMs’ ability to correct invalid SMILES and observe limited capability.
* We introduce **SmiSelf**, a cross-chemical language framework for invalid SMILES correction.

### Key Idea

SmiSelf converts invalid SMILES into SELFIES using grammar-guided rules, then leverages SELFIES’ guaranteed validity to produce corrected SMILES.

### Advantages

* ✅ Ensures **100% valid molecules**
* ✅ Preserves molecular characteristics
* ✅ Maintains or improves performance on other metrics
* ✅ Compatible with all SMILES-based generative models

---

<p align="center">
   <img src="https://github.com/wentao228/SmiSelf/img/framework.png" alt="Overview of SmiSelf" width="666px">
</p>

---

## ⚙️ Usage

### Functions

| Function          | Description                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------ |
| `smiself.encoder` | Converts an invalid SMILES string into a corresponding SELFIES string according to grammar rules |
| `smiself.decoder` | Converts a SELFIES string back into a valid SMILES string                                        |

---

### Example

#### Invalid SMILES → SELFIES → Valid SMILES

```python
invalid_smiles = "CC(=O)OC1=CC=CC=C1=C(=O)O)"

try:
    # Step 1: Invalid SMILES → SELFIES
    selfies = smiself.encoder(invalid_smiles)

    # Step 2: SELFIES → Valid SMILES
    valid_smiles = smiself.decoder(selfies)

except smiself.EncoderError:
    print("Encoding failed.")

except smiself.DecoderError:
    print("Decoding failed.")
```

---

## 📖 Citation

If you use this code in your research, please cite:

```bibtex
@inproceedings{tao2025make,
  title={How to Make Large Language Models Generate 100\% Valid Molecules?},
  author={Tao, Wen and Tang, Jing and Chan, Alvin and Hooi, Bryan and Bi, Baolong and Peng, Nanyun and Liu, Yuansheng and Wang, Yiwei},
  booktitle={Proceedings of the 2025 Conference on Empirical Methods in Natural Language Processing},
  pages={26576--26591},
  year={2025}
}
```

---

## 🙏 Acknowledgements

SmiSelf is built on top of the SELFIES:

[https://github.com/aspuru-guzik-group/selfies](https://github.com/aspuru-guzik-group/selfies)

---

## 📫 Contact

If you have any questions or collaboration interests, please feel free to reach out to Wen Tao ([taowen228@gmail.com](mailto:taowen228@gmail.com)) or open an issue.
