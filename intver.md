# 出题指引
## 总体说明

> 由于OJ需要让考生从控制台读取输入，所以咱们应该尽可能地方便考生读取数据；

> 因此，构建测试用例输入数据时，应该参考一些规范；

> 如果可能，最好使用我们的生成模版功能，这样考生只需完成一些核心函数，而不必写读取输入的逻辑。

## 出题生成模版

> 如上所述，我们在出题时，最好生成模版！

> 模版的入参支持的数据格式很丰富，例如：整型、长整型、浮点型、字符串型；以及这些所构成的一维、二维数组。

> 其他标准的基础数据类型也在陆续丰富中，例如：链表、二叉树、点等。

## 输入规范
### 单个数据
> 直接给出即可，无特别注意事项；

> 唯一要说明的事情，如果考察的是读取字符串，应该告诉考生，字符串中是否包含空格，以及字符串的长度范围。

### 单个数据之字符串
> 第一行应该给出字符串的长度n

```
例如：12
```

> 接下来一行，应该给出这个字符串

```
例如：Hello world!
```

> 最终示例：

```
12
Hello world!
```

### 一维数组
> 第一行应该告诉数组长度n

```
例如：3
```

> 第二行为空格分隔的数字；

```
例如，对于数组[1.2, 3.3, 2.6]，输入格式应该为：
1.2 3.3 2.6
```

> 特别的，对于字符串型一维数组，应该是接下来n行为数组内容，每行一个数组元素。

```
例如，对于数组["hello world 1", "hello world 2", "hello world 3"]，输入格式应该为：
hello world 1
hello world 2
hello world 3
```

> 最终示例

```
对于普通数组：[1.2, 3.3, 2.6]，构建的测试用例应该为：
3
1.2 3.3 2.6
```

```
对于字符串数组["hello world 1", "hello world 2", "hello world 3"]，构建的测试用例应该为：
3
hello world 1
hello world 2
hello world 3
```

### 二维数组
> 第一行应该告诉数组的行数m和列数n

```
例如：3 2
```

> 接下来m行，每行为n个空格分隔的数字

```
例如，对于数组[[1.2, 3.3, 2.6], [2.2, 4.3, 3.6]]，输入格式应该为：
1.2 3.3 2.6
2.2 4.3 3.6
```

> 特别的，对于字符串型二维数组，应该是接下来m*n行为数组内容，每行一个数组元素。

```
例如，对于数组[["hello world 1", "hello world 2", "hello world 3"], ["hello world 4", "hello world 5", "hello world 6"]]，输入格式应该为：
hello world 1
hello world 2
hello world 3
hello world 4
hello world 5
hello world 6
```

> 最终示例

```
对于普通数组：[[1.2, 3.3, 2.6], [2.2, 4.3, 3.6]]，构建的测试用例应该为：
3 2
1.2 3.3 2.6
2.2 4.3 3.6
```

```
对于字符串数组[["hello world 1", "hello world 2", "hello world 3"], ["hello world 4", "hello world 5", "hello world 6"]]，构建的测试用例应该为：
3 2
hello world 1
hello world 2
hello world 3
hello world 4
hello world 5
hello world 6
```

### 单链表ListNode类

> 待实现

### 点Point类

> 待实现

### 二叉树TreeNode类

> 待实现

### 其他常见的标准数据结构类

> 如果您认为有其他常见的标准数据结构类需要实现，可以联系qq：66014196@qq.com进行沟通。

> 或者在github上与我联系：https://github.com/acmcodercom/ojhtml

> 或者发邮件至：lifubang@acmcoder.com

> 或者在slack上一起交流：CodePapers

https://join.slack.com/t/codepapersworkspace/shared_invite/zt-vpse6e06-kFjSllp9QZgQWVfO2Lr9Dg