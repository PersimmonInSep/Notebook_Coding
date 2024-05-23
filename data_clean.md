### split()函数：
根据分割的规则，返回的是列表，若是没有满足分割规则，则返回原值；

对数据框的某一列进行批量操作的话：  
```python
# 5000(1:0.9) -> 5000
data["fixed_carport_num"] = data["fixed_carport_num"].str.split("(").str[0]
```
### python中的缺失值
在Python中，None 是一个特殊的对象，表示缺少值或者未定义值。而 NaN（Not a Number）是一种特殊的浮点数值，通常用于表示缺失或不可用的数据。在pandas中，NaN 也被用作缺失值的表示。
缺失值比较方面：None == None 是 True，但 NaN == NaN 是 False，这是因为 NaN 被认为是不可比较的

### re包相关函数
- re.search()
    - re.search() 用于在字符串中查找第一个匹配的子串。
    - 它返回一个匹配对象，如果找到了匹配，则该对象表示匹配的第一个子串；如果没有找到匹配，则返回 None。
    - 如果要获取匹配的具体内容，可以使用匹配对象的 group() 方法。例如：
```python
    # text = "地面150.00元/月"
    def extract_ground(text: str) -> str or None:
        if text is not None:
            match = re.search(r'地面(\d+\.\d+)', text)
            if match:
                return match.group(1)
        return None
```

- re.find()
    - re.findall() 用于在整个字符串中查找所有匹配的子串。
    - 它返回一个列表，其中包含了所有匹配的子串。
    - 如果没有找到任何匹配，返回一个空的列表 []。例如：
```python
    def build_year_clean(s: str) -> str or None:
        """
        把暂无替换成None,去除年份中的“年”，保留数字
        :param s: “2012年 2013年”
        :return: “2012 2013”
        """
        if s == "暂无":
            return None
        else:
            years = re.findall(r'(\d{4})年', s)
            years = " ".join(years)
            return years
```