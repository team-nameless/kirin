# kirin
An unopimized big ass OpenWebText-based LLM dedicated to what-you-know.

How to use:

```python
import torch
import torch.nn as nn

device = 'cuda' if torch.cuda.is_available() else 'cpu'

model = None

with open('kirin.pkl', 'rb') as f:
    model = pickle.load(f)

kirin = model.to(device)

prompt = input()
context_matrix = torch.tensor(encode(prompt), dtype=torch.long, device=device)
response = decode(kirin.generate(context_matrix.unsqueeze(0), max_new_tokens=150)[0].tolist())
```

