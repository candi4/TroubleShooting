# tqdm
Visualize progress

## Usage
### Basic
```python
for data_num in tqdm(range(100_000)):
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
## Represent text
### Dynamic description
  100%|███████████| 4/4 [00:11<00:00,  2.93s/it, bg_filename=image-asset.png]
```python
for i in tqdm(range(10)):
    pbar.set_postfix(bg_filename=bg_filename)
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