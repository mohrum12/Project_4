# Project_4
## Summary

This notebook evaluates how well **odor** and **cap color** predict mushroom **edibility** (UCI Agaricus–Lepiota dataset: `agaricus-lepiota.data`).  
I build three decision-tree classifiers:

| Model                | Features                 | Accuracy |
|----------------------|--------------------------|---------:|
| Odor Only            | one-hot odor dummies     | **0.9840** |
| Cap Color Only       | one-hot cap color dummies| 0.5869 |
| Combined             | odor + cap color dummies | **0.9869** |

**Key findings**
- **Odor is the dominant signal.** A model using only odor reaches **98.4%** accuracy and near-perfect precision/recall (see confusion matrix and classification report).
- **Cap color alone is weak.** At **58.7%** accuracy, cap color by itself performs only slightly better than chance and shows poor recall for the poisonous class.
- **Combining features yields only a marginal lift** over odor alone (**98.69% vs 98.40%**), indicating **odor drives nearly all predictive power** here.

**Why this matters**
- For quick, interpretable screening, odor is a highly informative attribute in this dataset.  
- Adding cap color increases model complexity with **minimal incremental benefit**, a useful lesson about focusing on **high-signal features** before broadening feature sets.

**Method notes**
- Preprocessing: mapped target `edibility` (`e`→0 edible, `p`→1 poisonous), created **one-hot** dummies for odor and cap color.
- Models: `DecisionTreeClassifier` (default) with a **70/30 train/test split** and fixed `random_state=42`.
- Evaluation: overall accuracy, **confusion matrices**, and full **classification reports** (precision/recall/F1).
