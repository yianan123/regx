# 正则表达式

## 1 正则表达式字符匹配

### 1.1 两种模糊匹

#### 1.1.1 横向模糊匹配
```
var regex = /ab{2,5}c/g;
var string = "abc abbc abbbc abbbbc abbbbbc abbbbbbc";
console.log( string.match(regex) );
// => ["abbc", "abbbc", "abbbbc", "abbbbbc"]
```
* 横向模糊指的是，一个正则可匹配的字符串的长度不是固定的，可以是多种情况的
* 其实现的方式是使用量词。譬如 {m,n}，表示连续出现最少 m 次，最多 n 次。
* g是修饰符表示全局匹配


#### 1.1.2 纵向模糊匹配
```
var regex = /a[123]b/g;
var string = "a0b a1b a2b a3b a4b";
console.log( string.match(regex) );
// => ["a1b", "a2b", "a3b"]

```
* 纵向模糊指的是，一个正则匹配的字符串，具体到某一位字符时，它可以不是某个确定的字符，可以有多种可能
* 其实现的方式是使用字符组。譬如 [abc]，表示该字符是可以字符 "a"、"b"、"c" 中的任何一个


### 1.2 字符组
1. 如 [123456abcdefGHIJKLM]，可以写成 [1-6a-fG-M]。用连字符 - 来省略和简写
2. 排除字符组 [^abc] 表示是一个除 "a"、"b"、"c"之外的任意一个字符。字符组的第一位放 ^（脱字符），表示求反的概念。
3. 常见的简写形式  

字符组 | 具体
---- | -----
\\d | 表示 [0-9]。表示是一位数字 
\\D | 表示 [^0-9]。表示除数字外的任意字符
\\w |表示 [0-9a-zA-Z_]表示数字、大小写字母和下划线。
\\W |表示 [^0-9a-zA-Z_]非单词字符。

### 1.3 量词

#### 1.3.1 简写形式
量词 | 具体含义
---- | -----
{m,} | 表示至少出现 m 次。
{m} | 等价于 {m,m}，表示出现 m 次。
? | 等价于 {0,1}，表示出现或者不出现。
\+ | 等价于 {1,}，表示出现至少一次。
\* | 等价于 {0,}，表示出现任意次，有可能不出现。