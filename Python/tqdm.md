# tqdm
Visualize progress

## Usage
### Basic
```python
from tqdm import tqdm
for data_order in tqdm(range(100_000)):
    pass
```
```python
from tqdm import tqdm
data_num = 100_000
with tqdm(total=data_num) as pbar:
    data_order = 0
    while data_order < data_num:
        data_order += 1; pbar.update(1)
```
```python
# >= python3.8
from tqdm import tqdm
for data_order in (pbar := tqdm(range(100_000))):
    pass
```
```python
from tqdm import tqdm
max_step = 1000
with tqdm(total=max_step, desc="Process") as pbar:
    step_count = max_step
    while step_count > 0:
        step_count -= 1
        pbar.n = max_step - step_count
        pbar.refresh()
```
## Represent text
### Dynamic description
  100%|███████████████| 10/10 [00:10<00:00,  1.01s/it, bg_filename=bg_filename9]
```python
for i in (pbar := tqdm(range(10))):
    pbar.set_postfix(bg_filename=f"bg_filename{i}")
```

### Logging
[tqdm) print대신에 tqdm을 이용해서 logging 방법](https://data-newbie.tistory.com/746)
### Static description
Example: 100%|████████| 1000/1000 [00:00<00:00, 1838800.53it/s]
```python
for i in tqdm(range(10), desc="Example"):
    pass
```
[Can I add message to the tqdm progressbar?](https://stackoverflow.com/questions/37506645/can-i-add-message-to-the-tqdm-progressbar)
### Print without interrupting the progress bar
```
loss: 9.60, acc: 0.04
loss: 9.70, acc: 0.03
loss: 9.80, acc: 0.02
loss: 9.90, acc: 0.01
100%|██████████████████████████████████████| 100/100 [00:11<00:00,  9.04it/s]
```
```python
for i in tqdm(range(100)):
    loss = i * 0.1
    acc = 1 - (i / 100)
    tqdm.write(f'loss: {loss:.2f}, acc: {acc:.2f}')
```