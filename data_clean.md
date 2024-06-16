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

### extract()
`extract()`方法和`search()`函数的作用是类似的，都用于从字符串中提取特定的模式或信息。但是它们在使用方式和适用场景上有一些区别：

1. **Pandas vs. re 模块**：
   - `extract()`是Pandas DataFrame/Series对象的方法，用于处理DataFrame中的字符串数据。
   - `re.search()`是Python标准库中re模块的函数，用于在普通的Python字符串中搜索匹配的模式。

2. **处理对象**：
   - `extract()`用于处理Pandas DataFrame/Series中的字符串列。
   - `re.search()`用于处理普通的Python字符串。

3. **返回结果**：
   - `extract()`返回一个新的Pandas Series，其中包含从字符串中提取的信息。
   - `re.search()`返回一个匹配对象，需要使用其方法（如`group()`）来提取匹配的信息。

在实际使用中，如果你处理的数据是DataFrame，特别是需要在DataFrame的某一列中提取信息，那么使用`extract()`会更方便。但如果你只需要在普通的字符串中搜索和提取信息，则使用`re.search()`会更合适。

如果`extract()`方法在字符串中没有找到满足条件的模式，它将返回NaN（Not a Number），这是Pandas中表示缺失值的标记。

`extract()`方法可以处理包含空值的列。当对包含空值的列使用extract()时，它会忽略空值，并在非空值的字符串上执行提取操作。

例如：
```python
    # community_link - "https://xm.anjuke.com/community/view/352783"
    # community_cd   - "352783"
    data["community_cd"] = data["community_link"].str.extract(r'(\d+)') 
```

### 获取数据框中，最近一个月的数据
```python
    import pandas as pd
    from datetime import datetime, timedelta

    # 创建一个示例 DataFrame
    data = {'date_str': ['2024-04-15', '2024-05-10', '2024-05-20', '2024-06-01']}
    df = pd.DataFrame(data)

    # 将 'date_str' 列转换为时间列
    df['date'] = pd.to_datetime(df['date_str'])

    # 获取当前日期
    current_date = datetime.now()

    # 计算最近一个月的开始日期
    one_month_ago = current_date - timedelta(days=30)

    # 筛选出最近一个月的数据
    recent_data = df[df['date'] >= one_month_ago]

    # 输出结果
    print(recent_data)
```

111
