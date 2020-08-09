# Markdown极简入门

## 段落
采用空行进行段落切换。
注意如下格式：
```markdown
第一段。

第二段。
前面没有换行，还是第二段。
```
效果如下：AMLab_toolbox

>第一段。
>
>第二段。
>前面没有换行，还是第二段。

## 字体样式
一般支持加粗、斜体、删除三种字体样式，格式如下：

```markdown
**加粗**

*斜体*

~~删除~~
```

效果如下：

**加粗**

*斜体*

~~删除~~

## 标题
使用#，可表示1-6级标题，规则如下：
```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

上述Markdown的显示效果如下：
> # 一级标题
> ## 二级标题
> ### 三级标题
> #### 四级标题
> ##### 五级标题
> ###### 六级标题

## 列表
正如word中，Markdown里的“列表”有无序、有序之分，还可以包含层次性。
### 无序列表
使用*、-、+标记无序列表，如：
```markdown
- item one
- item two
- item three
```

注意：标记后面最少有一个空格。效果如下：
- item one
- item two
- item three


### 有序列表
使用数字和.标记有序列表，如：
```markdown
1. item one
2. item two
3. item three
```

注意：标记后面最少有一个空格。效果如下：
1. item one
2. item two
3. item three

### 任务列表
采用-和[ ]/[x]组合添加任务列表。注意,
```markdown
- [x] 任务1，已完成
- [ ] 任务2， 未完成（注意，方括号里有空格）
```

效果如下：
> - [x] 任务1，已完成
> - [ ] 任务2， 未完成（注意，方括号里有空格）

### 多层列表
如果要用多层列表，可以采用制表符（Tab键）进行控制。

```markdown
1. item one
    * one
    * two
2. item two
3. item three
    * one
        - [x] one
        - [ ] two
    * two
```
效果如下：

1. item one
    * one
    * two
2. item two
3. item three
    * one
        - [x] one
        - [ ] two
    * two

## 引用
用>开启引用，相关内容会在引用块中展示。规则如下：
```markdown
> 引用
>
> 引用
>> 二级引用

```
效果如下：
> 引用
>
> 引用
>> 二级引用


## 插入代码
如果想在文字中插入代码段，可以采用一对```包括代码即可。
本文档中在展示Markdown代码时就采用了这种方式呈现。
如下形式：

```python
print('Hello Markdown')
```

## 插入链接
```markdown
[baidu](www.baidu.com)
```
效果如下：
[Baidu](www.baidu.com)

## 插入表格


## 数学公式

 
## 插入图片


## References
* [Mastering Markdown (from GitHub)](https://guides.github.com/features/mastering-markdown/)
