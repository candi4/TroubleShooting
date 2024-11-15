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
### Represent text
  3%|█▏                                           | 2513/100000 [05:37<3:13:25,  8.40it/s, bg_filename=image-asset.png]
```python
for i in tqdm(range(10)):
    pbar.set_postfix(bg_filename=bg_filename)
```
### Logging
[tqdm) print대신에 tqdm을 이용해서 logging 방법](https://data-newbie.tistory.com/746)
