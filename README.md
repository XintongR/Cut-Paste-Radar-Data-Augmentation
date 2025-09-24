# Cut-Paste Radar Data Augmentation (Demo)

A clean, **confidentiality-safe** demo of a Cut-Paste data augmentation strategy for **4d radar point clouds**.  
The original work was part of my Master's thesis on improving **CNN-based 3D object detection**.  
This repository uses **toy data** to illustrate the idea—no private datasets or partner code are included.

## 🚦 Why Cut-Paste for Radar?
High-quality radar annotations are scarce, especially for diverse scenarios.
**Cut-Paste** increases scene diversity by inserting realistic object instances at new, valid locations while keeping labels consistent.
This can improve generalization for 3D detection models.

## ✨ What’s Included
- Minimal, dependency-light **demo implementation** (`cut_paste_module.py`)
- **Collision checking** (2D BEV IoU) to avoid overlapping boxes
- End-to-end **toy example & visualization** (`demo_cutpaste.py`)
- No confidential code, no proprietary datasets

## 📂 Project Structure
```
radar-cutpaste-demo/
│── cut_paste_module.py      # Core Cut-Paste augmentation
│── demo_cutpaste.py         # Toy example + before/after visualization
│── README.md                # Documentation
│── requirements.txt         # Minimal dependencies
└── docs/
    ├── before.png           # (Optional) Example visualization
    └── after.png            # (Optional) Example visualization
```


## 🧩 Data Interfaces
`data_dict` (I/O):
```python
{
  "frame_id": "00001",
  "training": True,
  "points": np.ndarray (N, 7),   # [x, y, z, RCS, v_r, v_r_comp, t] — toy values in demo
  "gt_boxes": np.ndarray (M, 7), # [x, y, z, dx, dy, dz, heading]
  "gt_names": np.ndarray (M,)
}

config (demo):
{
  "Augmentation Probability": 1.0,
  "DISABLE_AUG_LIST": ["velocity_calculation", "rcs_calculation"]  # ignored in demo
}
```

## 🛠 Installation
```bash
pip install -r requirements.txt
```

## ▶️ Quick Start
```python
python demo_cutpaste.py
```
This shows a side-by-side plot of before vs after augmentation.

To save images used in README, add:
```python
plt.savefig("docs/before.png"); plt.savefig("docs/after.png")
```

## 🔒 Confidentiality & Scope

This is a public demo. All proprietary data and partner-specific code are removed or replaced by synthetic examples. Licensed under MIT.

## 📄 License
MIT License — research & education friendly.
