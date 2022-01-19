# 总体说明

> 出题官请移步这里：[出题指引](https://labfiles.acmcoder.com/ojhtml/index.html?v=1#/intver)

> 所有的测试用例输入，最后一行都有一个回车"\n"！！！

> Linux系统，文件名大小写敏感，在c/c++引用头文件时尤其需要注意；

> 读取输入时，不要自行加提示消息，例如：```raw_input('Please input two numbers: ')```；

> 输出答案时，不要自行添加提示消息，例如：```printf("My answer is:\n")```；

> 答案输出完毕时，不要让控制台等待，例如：```system("pause")```；

> 您的程序只能从标准输入（stdin，即“键盘”）读入，并输出到标准输出（stdout，即“屏幕”）；

> 不允许操作文件或者访问网络，否则将导致不正确的结果；

> 请不要引用不必要的头文件或命名空间。

# 输出超限解释

> 在我们检测您的程序输出时，发现输出的字符个数比正确答案多了，所以不用比对，已经是错误的；

> 这个时候就会给您返回输出超限，其实您可以认为就是答案错误。

# 输入输出

## OJ运行原理：

```bash
for usercase in `ls .`
do
  cat $usercase | 你的脚本或编译后的程序 > test.out
done
```
也就是说，后台每一个测试用例都会重启您的应用。

## 注意事项
> 您的程序需要从stdin读入数据，并输出到stdout；

> 数据的输入输出格式请遵循题目的描述。

## 可能遇到的坑（持续补充中ing）

> 有些题目是客户自己出的，可能描述不会很人性化，我们监控到后台提问时会及时发布公告进行说明，请留意公告，并看清楚测试样例（*注意是真实的样例输入，而不是样例描述*，有的时候描述可能会有瑕疵，但是真实的样例输入是经过代码验证的）；

> 有些输入说明告诉你是输入一个整数n，一般的输入样例肯定是真的给你一个整数，但是，有些客户出题会是n=3；带上“n=”这2个字符。

> 有些输入说明告诉你是输入一个数组arr，一般输入的样例是n个空格分隔的数字，但是，有些客户出题会是[1,2,3,4,5]，您读到的输入有中括号，以及逗号，而且逗号前后可能还有空格。

> 关于为什么不提供类似于leetcode的免输入输出模式，这个需要后台录题时录入模版，我们后台是支持免输入输出模式的，但是很少客户使用；我们理解可能是功能不完善，如果有愿意加入我们的，请发送简历至"postmaster@acmcoder.com"。

> 陆续补坑......

## “奇怪”的输入输出

### 说明
> 目前，赛码网有大一半的题目都是客户自己的出题官出的，也就是说可能是你未来的同事出的；

> 对于这些题目的输入输出，可能会有些直接，需要考生多编写点输入输出代码；

> 我们尽量在改进出题系统的核心函数模式，让更多的出题官愿意使用核心函数模式；

> 有些考生可能要吐槽，客户自己出的题目，赛码网为什么不改进下题目的输入输出？

这个问的很好，因为目前赛码网的编程题的出题量是巨大的，根本审核不过来，只要题目能跑通，题目就是合格的。

### 没有给出矩阵的行列数
```
有些输入可能是：
输入一个矩阵，每行以空格分隔。
3 2 3
1 6 5
7 8 9
```

> 对于这种没有给定矩阵行列数的输入，我们只能按照字符串拆分来进行。

> python
```python3
#!/usr/bin/env python  
# coding=utf-8
arr = []
while 1:
    s = input()

    if s != "":
        arr.append(list(map(int, s.split())))
    else:
        break
# 使用自测数据按钮时调试用，正式提交时要删掉。
print(arr)
```

> js

```js
let arr = [];
let line;
while ((line = read_line()) != "") {
    arr.push(line.split(' ').map(v=>parseInt(v)));
}
// 使用自测数据按钮时调试用，正式提交时要删掉。
for (let i=0; i<arr.length; i++) {
    for (let j=0; j<arr[i].length; j++) {
        printsth(arr[i][j], ' ');
    }
    print();
}
```

> java

```java
import java.io.*;
import java.util.*;

class Solution {
    public void myFunc(ArrayList<ArrayList<Integer>> arr) {
        // 使用自测数据按钮时调试用，正式提交时要删掉。
        System.out.println(arr);
    }
}
public class Main
{
    public static void main(String args[])
    {
        Scanner cin = new Scanner(System.in);
        ArrayList<ArrayList<Integer>> arr = new ArrayList<ArrayList<Integer>>();
        while(cin.hasNextLine())
        {
            ArrayList<Integer> row = new ArrayList<Integer>();
            String line = cin.nextLine();
            if (line.length() > 0) {
                String[] arrLine = line.split(" ");
                for (int i=0; i<arrLine.length; i++) {
                    row.add(Integer.parseInt(arrLine[i]));
                }
                arr.add(row);
            }
        }
        
        new Solution().myFunc(arr);
    }
}
```

> c

```c
#include <stdio.h>
int main()
{
    int arr[1024][1024];
    int row = 0, col = 0, j = 0;
    char c;
    while(scanf("%d", &arr[row][j]) != EOF) {
        c = getchar();
        if (row == 0) col++;
        if (c == '\n') {
            row++;
            j = 0;
        } else if (c == ' ') {
            j++;
        }
    }
    // 使用自测数据按钮时调试用，正式提交时要删掉。
    printf("rows: %d, cols: %d\n", row, col);
    for (int i=0; i<row; i++) {
        for (int k=0; k<col; k++) {
            printf("%d ", arr[i][k]);
        }
        printf("\n");
    }
}
```

> c++

```c++
#include <iostream>
#include <vector>
#include <string>
#include <sstream>
using namespace std;
int main() {
    vector<vector<int>> arr;
    string input;
    while (getline(cin, input)) {
        if (input.size() > 0) {
            stringstream stringin(input);
            int num;
            vector<int> a;
            while (stringin >> num) {
                a.push_back(num);
            }
            arr.push_back(a);
        }
    }
    // 使用自测数据按钮时调试用，正式提交时要删掉。
    cout << "rows: " << arr.size() << ", cols: " << arr[0].size() << endl;
    for (int i=0; i<arr.size(); i++) {
        for (int j=0; j<arr[i].size(); j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }
}
```

### Js读取超长字符串

> 由于read_line()只能读取1024个字符，所以如果题目中的用例涉及到长度大于1024字符串的，需要用到gets(n)这个函数。

```
例如有这样一个题目，读取一个字符串，计算其长度。
备注：字符串的长度范围为1到10000;
代码一般这么写：
```

```js
let line = gets(10000);
print(line.length);
```

```
如果测试用例长度刚好10000，则没有问题。
如果测试用例长度为小于10000，假设是100，则您的答案为101，错误。
因为gets(n)函数在遇到回车，或者第n个字符时，都会结束，但是如果是遇到回车结束的，则回车也会包含在返回值当中，所以，应该trim一下。
```

```js
let line = gets(10000).trim();
print(line.length);
```

### 输入数组中带有中括号和逗号
```
有些输入可能是，输入一个矩阵：
[[3,2,3],
 [1,6,5],
 [7,8,9]]
```

> 对于这种没有给定矩阵行列数的输入，而且还包含中括号和逗号的输入，我们也是只能按照字符串拆分来进行。

这里逗号和右中括号是关键。

> python
```python3
#!/usr/bin/env python  
# coding=utf-8
arr = []
while 1:
    s = input()

    if s != "":
        arr.append(list(map(int, s.replace("],", "").replace(" ", "").replace("[", "").replace("]", "").split(","))))
    else:
        break
# 使用自测数据按钮时调试用，正式提交时要删掉。
print(arr)
```

> js

```js
let arr = [];
let line;
while ((line = read_line()) != "") {
    arr.push(line.replace(/\]\,/g, "").replace(/ /g, "").replace(/\[/g, "").replace(/\]/g, "").split(",").map(v=>parseInt(v)));
}
// 使用自测数据按钮时调试用，正式提交时要删掉。
for (let i=0; i<arr.length; i++) {
    for (let j=0; j<arr[i].length; j++) {
        printsth(arr[i][j], ' ');
    }
    print();
}
```

> java

```java
import java.io.*;
import java.util.*;

class Solution {
    public void myFunc(ArrayList<ArrayList<Integer>> arr) {
        // 使用自测数据按钮时调试用，正式提交时要删掉。
        System.out.println(arr);
    }
}
public class Main
{
    public static void main(String args[])
    {
        Scanner cin = new Scanner(System.in);
        ArrayList<ArrayList<Integer>> arr = new ArrayList<ArrayList<Integer>>();
        while(cin.hasNextLine())
        {
            ArrayList<Integer> row = new ArrayList<Integer>();
            String line = cin.nextLine().trim();
            if (line.length() > 0) {
                String[] arrLine = line
                    .replace("],", "")
                    .replace(" ", "")
                    .replace("[", "")
                    .replace("]", "")
                    .split(",");

                for (int i=0; i<arrLine.length; i++) {
                    row.add(Integer.parseInt(arrLine[i]));
                }
                arr.add(row);
            }
        }
        
        new Solution().myFunc(arr);
    }
}
```

> c

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
    int arr[1024][1024];
    char buf[1024];
    char *tok;
    
    int row = 0, col = 0, j = 0;
    while(NULL != gets(buf)) {
        if (strlen(buf) > 0) {
            tok = strtok(buf, " ,[]");
            while (tok != NULL) {
                arr[row][j++] = atoi(tok);
                if (row == 0) col++;
                tok = strtok(NULL, " ,[]");
            }
            row++, j = 0;
        }
    }
    // 使用自测数据按钮时调试用，正式提交时要删掉。
    printf("rows: %d, cols: %d\n", row, col);
    for (int i=0; i<row; i++) {
        for (int k=0; k<col; k++) {
            printf("%d ", arr[i][k]);
        }
        printf("\n");
    }
}
```

> c++

```c++
#include <iostream>
#include <vector>
#include <string>
#include <string.h>
#include <sstream>
using namespace std;
int main() {
    vector<vector<int>> arr;
    string input;
    char *tok;
    while (getline(cin, input)) {
        if (input.size() > 0) {
            vector<int> a;
            tok = strtok((char *)input.c_str(), " ,[]");
            while (tok != NULL) {
                a.push_back(stoi(tok));
                tok = strtok(NULL, " ,[]");
            }
            arr.push_back(a);
        }
    }
    // 使用自测数据按钮时调试用，正式提交时要删掉。
    cout << "rows: " << arr.size() << ", cols: " << arr[0].size() << endl;
    for (int i=0; i<arr.size(); i++) {
        for (int j=0; j<arr[i].size(); j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }
}
```

### 输出数组或矩阵

> 有些时候，出题人可能是直接用python进行的验题，输出二维数组时，是带有中括号和逗号的。

```python3
arr = [[1,2,3],[4,5,6]]
print(arr)
```
输出是：
```
[[1, 2, 3], [2, 3, 4]]
```

```
输出已经拼好了中括号和逗号，但是，别的语言就没有这么幸运，需要自己拼凑这些。
```

> js

```js
let arr = [[1,2,3],[4,5,6]]
console.log(arr.toString())
// 输出是：1,2,3,4,5,6
// 这样就错了，没有中括号

console.log(JSON.stringify(arr));
// 这样是对的

// 这样也是可以的
printsth('[');
for (let i=0; i<arr.length; i++) {
    printsth('[');
    printsth(arr[i].join(', '));
    printsth(']');
    if (i < arr.length - 1)
        printsth(', ');
}
print(']');
```

## 自测模式
> 您可以使用编程界面的“自测数据”进行样例数据或自定义数据的调试；

> 样例数据您需要自行从题干拷贝粘贴到自测数据中；（后续产品升级时，会替您录入第一个样例数据到自测数据中）

> 您可以添加多个自定义数据；

## 提交及计算成绩
> 在非“自测数据”状态下，点击调试按钮，就算最后的提交；

> 我们只取最后一次的提交计算最终成绩。

# Java
## 版本
> 1.8.0_66
```bash
root@oj-tk2sd:/# java -version
java version "1.8.0_66"
Java(TM) SE Runtime Environment (build 1.8.0_66-b17)
Java HotSpot(TM) 64-Bit Server VM (build 25.66-b17, mixed mode)
root@oj-tk2sd:/# javac -version
javac 1.8.0_66
root@oj-tk2sd:/#
```

## 编译命令
```javac -encoding UTF8 Main.java```

## 运行命令
```cat usercase.in | java Main```

## 类名：public class Main
> 根据编译命令和运行命令，我们可以得出：

不要自定义包名称，否则会报错，即不要添加package answer之类的语句；

您可以写很多个类，但是必须有一个类名为Main，并且为public属性，并且Main为唯一的public class；

Main类的里面必须包含一个名字为'main'的静态方法（函数），这个方法是程序的入口。

## 示例代码
```java
//package main
//注意不要添加包名称，否则会报错。

import java.io.*;
import java.util.*;
class Solution {
    public int addab(int a, int b) {
        return a+b;
    }
}
public class Main
{
    public static void main(String args[])
    {
        Scanner cin = new Scanner(System.in);
        int a, b;
        while(cin.hasNextInt())
        {
            a = cin.nextInt();
            b = cin.nextInt();
            Solution s = new Solution();
            int c = s.addab(a, b);
            System.out.println(c);
        }
    }
}
```

# Python3
## 版本
> Python 3.4.3

## 缩进
> 缩进可以使用tab、4个空格或2个空格，但是只能任选其中一种，不能多种混用;

## 输入特殊说明
> 如果使用sys.stdin.readline，因为默认会带换行符，所以要strip('\n')进行截取；

> 使用input()则不会。

## 可以使用numpy
> version: 1.15.1

## 示例代码
```python
#!/usr/bin/env python  
# coding=utf-8  
# Python使用的是3.4.3，缩进可以使用tab、4个空格或2个空格，但是只能任选其中一种，不能多种混用
while 1:
    a=[]  
    s = input()

    if s != "":
        for x in s.split():  
            a.append(int(x))  

        print(sum(a))
    else:
        break
```

# Python2
## 版本
> Python 2.7.6

## 缩进
> 缩进可以使用tab、4个空格或2个空格，但是只能任选其中一种，不能多种混用;

## 输入特殊说明
> 如果使用sys.stdin.readline，因为默认会带换行符，所以要strip('\n')进行截取；

> 使用raw_input()则不会。

## 可以使用numpy
> version: 1.15.1

## 示例代码
```python
#!/usr/bin/env python  
# coding=utf-8  
# Python使用的是2.7.6，缩进可以使用tab、4个空格或2个空格，但是只能任选其中一种，不能多种混用
while 1:
    a=[]  
    s = raw_input()
    # raw_input()里面不要有任何提示信息
    if s != "":
        for x in s.split():  
            a.append(int(x))  

        print sum(a)
    else:
        break
```

# javascript
## 版本
> Google V8 Engine(6.2.340)

## 输入API
### 读取一行输入
> read_line()

> 将读取至多1024个字符，当还未达到1024个时如果遇到回车或结束符，提前结束。

> 读取多行最简单的办法是while((line = read_line()) != '')。

> 或者使用下一个API。

### 读取n个字符
> gets(n)

> 将读取至多n个字符，当还未达到n个时如果遇到回车或结束符，会提前结束。

> 回车符可能会包含在返回值中。

### 读取一个（长）整数
> readInt()

### 读取一个浮点型
> readDouble()

## 输出API
### 不加回车的输出
> printsth(sth, ...)

> 往控制台输出sth，当有多个参数时，空格分隔；最后不加回车。

### 带回车的输出
> print(sth, ...)

> console.log(sth, ...)

> 往控制台输出sth，当有多个参数时，空格分隔；最后加回车。

## 示例代码1
```js
var a, b;
var solveMeFirst = (a,b) => a+b;
while((a=readInt())!=null && (b=readInt())!=null){
    let c = solveMeFirst(a, b);
    print(c);
}
```

## 示例代码2
```js
var line;
var solveMeFirst = (a,b) => a+b;
while((line = read_line()) != ''){
    let arr = line.split(' ');
    let a = parseInt(arr[0]);
    let b = parseInt(arr[1]);
    let c = solveMeFirst(a, b);
    print(c);
}
```

## V8源码
> https://github.com/acmcodercom/v8/tree/forstdio_baseon_6.2.340/samples

# Nodejs
## 版本
> 6.9.1

## 输入输出
> process.stdin、process.stdout

> readline

> node-stdio (https://www.npmjs.com/package/node-stdio)

## 示例代码1
```js
var cmd = require('node-stdio')
var a, b;
var solveMeFirst = (a,b) => a+b;
while((a=cmd.readInt())!=null && (b=cmd.readInt())!=null){
    let c = solveMeFirst(a, b);
    cmd.print(c);
}
```

## 示例代码2
```js
process.stdin.resume();
process.stdin.setEncoding('utf-8');
 
var input = "";
var input_array = "";

//这里不灵活，需要全部读取数据后再处理，容易超内存。
process.stdin.on('data', function (data) {
    input += data;
});

var solveMeFirst = (a, b) => a+b;

process.stdin.on('end', function () {
    let arr = input.split("\n");
    for (var i=0; i<arr.length; i++) {
	    if (arr[i] != '') {
            input_array = arr[i].split(" ");
            
            let inline = 0;
            let res;
            let _a = parseInt(input_array[inline].trim(), 10);
            inline += 1;
        
            let _b = parseInt(input_array[inline].trim(), 10);
            inline += 1;
        
            res = solveMeFirst(_a, _b);
            process.stdout.write("" + res + "\n");
	    }
    }
});
```

## 示例代码3
```js
var readline = require('readline');
process.stdin.setEncoding('utf-8');

var rl = readline.createInterface({input: process.stdin, output: process.stdout, prompt:''});
rl.prompt();

var solveMeFirst = (a, b) => a+b;

rl.on('line', function (data) {
    let arr = data.split(' ');
    if (arr && arr.length==2) {
        let c = solveMeFirst(+arr[0], +arr[1]);
        process.stdout.write('' + c + '\n');
    }
});
```

# SQL
## 题型
> SQL分为2中题型，sqlite3和mysql8；

> 有些客户只考sqlite3，有些客户只考mysql8。

## sqlite3
> SQLite3支持标准的SQL语法

具体见：https://labfiles.acmcoder.com/sqlite-doc/lang.html；

> SQLite3内置支持的有些函数与其他数据库不同

具体见：https://labfiles.acmcoder.com/sqlite-doc/lang_corefunc.html。

## mysql
> 版本：8.0.24

> 默认安装，所以表名和列名大小写敏感（后期有可能改为大小写不敏感）。

# C语言
## 版本：5.4.0
```bash
root@oj-tk2sd:/# gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/5/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 5.4.0-6ubuntu1~16.04.12' --with-bugurl=file:///usr/share/doc/gcc-5/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-5 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-5-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-5-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-5-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release--build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.12)
```

## 编译命令
```bash
gcc Main.c -o Main -O2 -fno-asm -Wall -lm -static -std=c99
```

## 示例代码
```c
#include <stdio.h>
int main()
{
   int a, b;
   while(scanf("%d%d", &a, &b) != EOF)
      printf("%d\n", a + b);
}
```

# C++
## 版本 5.4.0
```bash
root@oj-tk2sd:/# g++ -v
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/5/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 5.4.0-6ubuntu1~16.04.12' --with-bugurl=file:///usr/share/doc/gcc-5/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-5 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-5-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-5-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-5-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release--build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.12)
```

## 编译命令
```bash
g++ Main.cc -o Main -O2 -fno-asm -Wall -lm -static -std=c++11 -lrt -Wl,--whole-archive -lpthread -Wl,--no-whole-archive
```

## 示例代码
```c++
#include  <iostream> 
using namespace std;
int main()
{
    int a, b;
    while(cin>> a >> b)
    cout << a + b << endl;
    return 0;
}
```

## 建议使用scanf
> 读取输入时，建议使用scanf代替cin，因为对于大规模数据时，由于cin的内部实现原理，容易超时。

# clang
## 版本 7.0.1
> clang version 7.0.1 (tags/RELEASE_701/final)

## 编译命令
```bash
clang Main.c -o Main -fno-asm -Wall -lm -static -std=c99
```

# clang++
## 版本 7.0.1
> clang version 7.0.1 (tags/RELEASE_701/final)

## 编译命令
```bash
clang++ Main.cc -o Main -I/usr/include/c++/4.8 -I/usr/include/x86_64-linux-gnu/c++/4.8 -fno-asm -Wall -lm -static -std=c++11 -lrt -Wl,--whole-archive -lpthread -Wl,--no-whole-archive
```

# golang
## 版本 1.2.1
> go version go1.2.1 linux/amd64

> go version go1.13.15 linux/amd64 灰度中...

## 编译命令
```bash
go build -o Main.exe -p 1 Main.go
```

## 示例代码
```go
package main
import "fmt"
import "io"
func main() {
  a:=0
  b:=0
  for {
    _, err := fmt.Scanf("%d%d",&a,&b)
    if err != nil {
        if err == io.EOF {
            break
        }
    } else {
		fmt.Printf("%d\n",a+b)
	}
  }
}
```

# ruby
## 版本 1.9.3p484
> ruby 1.9.3p484 (2013-11-22 revision 43786) [x86_64-linux]

## 编译命令
```bash
ruby -c Main.rb
```

## 示例代码
```ruby
a=gets
while a != nil && a != "" && a != "\r" && a != "\n" do
    arr = a.split(" ")
    sum = 0
    arr.each_with_index do |value, index|
        sum = sum + value.to_i
    end
    puts sum.to_s
    a=gets
end
```

# bash
## 版本
> GNU bash, version 4.3.11(1)-release (x86_64-pc-linux-gnu)

## 示例代码
```bash
#!/bin/bash
 
read -a arr
#echo ${#arr[@]}
while [ ${#arr[@]} -eq 2 ]
do
sum=$((${arr[0]}+${arr[1]}))
echo "$sum"
read -a arr
done
```

# Swift
## 版本
> Swift version 4.2.3

## 示例代码
```swift
import Foundation

var ab = readLine() ?? "break"
while ab != "break"
{
  let array = ab.split(separator: " ")
  let a = Int(array[0])!
  let b = Int(array[1])!
  print(a+b)
  ab = readLine() ?? "break"
}
```

# Lua
## 版本
> Lua 5.3.2

## 示例代码
```lua

local count = 0
function string.split(str, delimiter)
	if str==nil or str=='' or delimiter==nil then
		return nil
	end
	
    local result = {}
    for match in (str..delimiter):gmatch("(.-)"..delimiter) do
        table.insert(result, match)
    end
    return result
end
while true do
	local line = io.read()
	if line == nil or line == "" then break end
	local tb = string.split(line, " ")
	local sum = 0
	for i=1, #tb do
		local a = tonumber(tb[i])
		sum = sum+a
	end
	if count>0 then
		io.write("\n")
	end
	io.write(string.format("%d", sum))
	count = count+1
end
```

# PHP
## 版本
> PHP 5.5.9-1ubuntu4.14 (cli)

## 示例代码
```php
<?php
function solveMeFirst($a,$b){
    return $a + $b;
}
$handle = fopen ("php://stdin","r");
$s = fgets($handle);
while ($s != "") {
	$a = explode(" ", $s);
	$sum = solveMeFirst((int)$a[0],(int)$a[1]);
	print ($sum);
	print ("\n");
	$s = fgets($handle);
}
fclose($handle);
?>
```

# R语言
## 版本
> R3.4.1

## 示例代码
```r
con <- file("stdin", "r")  
a = readLines(con, n = 1)
b = readLines(con, n = 1)
while (a!="" && b!="") {
  c = as.numeric(a) + as.numeric(b)
  cat(format(c, scientific = FALSE))
  cat('\n')
  a = readLines(con, n = 1)
  b = readLines(con, n = 1)
}
close(con)
```