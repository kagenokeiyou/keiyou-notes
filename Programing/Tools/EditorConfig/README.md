# EditorConfig

<https://editorconfig.org>

## 什么是 EditorConfig

EditorConfig 是一个帮助多个开发者在不同的编辑器和 IDE 上维护一致的编码风格的工具。

## 配置文件

配置文件是 `.editorconfig` 文件。

EditorConfig 文件使用与 Python configparser 库所使用的格式兼容的 INI 格式，但在节名称中允许使用 `[` 和 `]` 。节名称是文件路径通配符（区分大小写），类似于 gitignore 接受的格式。仅使用正斜杠（ `/` ，而不是反斜杠）作为路径分隔符，并使用井号（ `#` ）或分号（ `;` ）作为注释。注释应单独放在一行。EditorConfig 文件应使用 UTF-8 编码，并使用 CRLF 或 LF 行分隔符。EditorConfig 文件按从上到下的顺序读取，找到的最新规则具有优先权。

通配符模式：

|模式          |描述           |
|--------------|---------------|
|`*`           |匹配任何字符字符串，但不包括路径分隔符|
|`**`          |匹配任意字符序列|
|`?`           |匹配任意单个字符|
|`[name]`      |匹配 name 中的任意单个字符|
|`[!name]`     |匹配不在 name 中的任意单个字符|
|`{s1,s2,s3}`  |匹配任意给定的字符串（用逗号分隔）|
|`{num1..num2}`|匹配介于 num1 和 num2 之间的任何整数，其中 num1 和 num2 可以是正数或负数|

```ini
root = true

[*]
charset = utf-8
indent_style = space
indent_size = 4
end_of_line = lf
trim_trailing_whitespace = true
insert_final_newline = true

[*.{html,js,ts,vue}]
indent_size = 2

[*.{json,yml,yaml}]
indent_size = 2
```
