### 1. substring()
```
格式：substring(开始位置,结束位置)
要点描述：
该方法返回一个新的字符串；
当第二个参数不传时，则默认为最后一个字符后面的位置；
当参数为负数时，该参数会自动转为0
PS：特殊情况，当结束位置小于开始位置时，当以小的位置为起点，大的为结束
```
### 2. substr()

```
格式：substr(开始位置,字符个数)
要点描述：
当第一个参数为负数时，该参数会加上该字符串长度，再用于开始位置；
当第二个参数为负数时，该参数会自动转为0
```
### 3. slice()

```
格式：slice(开始位置,结束位置)
要点描述：
当参数为负数时，该参数将与字符串的长度相加
```