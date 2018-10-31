# Tiny+ 编译器部分实现

## 一) 词法分析
* 问题:
    * `{abc er` 缺少右闭合怎么处理? 直接默认一整行错误,并跳过该行分析
    * `abc ef}` 缺少左闭合怎么处理? 直接默认一整行错误,并跳过该行分析
    * 换行符的处理
    ```cpp
    //c++ 字符串包含换行符
        std::string str = "a"
                          "b";
        std::string str2 = "a\n\a";
    ```
    目前我在字符串状态下,匹配到了`\n`会认为是失败的.