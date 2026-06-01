# PyTorch Lesson 05 — Dataset and DataLoader

**Time:** 3–4 hours  
**Prerequisite:** [Lesson 04](04-training-loop.md)

## Custom Dataset

```python
from torch.utils.data import Dataset, DataLoader

class TabularDataset(Dataset):
    def __init__(self, features, labels):
        self.X = torch.tensor(features, dtype=torch.float32)
        self.y = torch.tensor(labels, dtype=torch.float32)

    def __len__(self):
        return len(self.X)

    def __getitem__(self, idx):
        return self.X[idx], self.y[idx]

loader = DataLoader(dataset, batch_size=32, shuffle=True, num_workers=0)
```

On Mac/Windows, start with `num_workers=0`; on Linux you can try `2` later.

## CSV loading example

```python
import pandas as pd

df = pd.read_csv("data.csv")
X = df[["feat1", "feat2"]].values
y = df["target"].values
```

---

## Exercises

Folder: `~/python-hero/practice/pytorch/lesson05/`

### Exercise 1 — Custom Dataset

100 samples, 3 features, target = sum of features + noise. Build `Dataset` + `DataLoader` batch 16.

**Check:** [Answer](../answers/05-dataloader-answers.md#exercise-1--custom-dataset)

### Exercise 2 — Iterate one epoch

Print shape of first 3 batches (`x.shape`, `y.shape`).

**Check:** [Answer](../answers/05-dataloader-answers.md#exercise-2--iterate-one-epoch)

### Exercise 3 — CSV pipeline

Create `data.csv` with columns `x1,x2,y`. Load with pandas, train MLP 10 epochs.

**Check:** [Answer](../answers/05-dataloader-answers.md#exercise-3--csv-pipeline)

---

[All answers](../answers/05-dataloader-answers.md) · **Next:** [Lesson 06](06-cnns-for-images.md)
