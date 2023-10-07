# Gugle的代码风格指南

* 版本： `0.0.1`
* 创建日期： `2023/10/07`
* 最后修改： `2023/10/07`

## 通用

* 缩进：
    * 缩进应使用 `空格` 而非 `制表符`
    * 除非一些特殊需求，否则一般使用 `4` 个 `空格` 作为缩进

* 操作符
    * 三元操作符、二元操作符通常情况下前后需要有空格，如：
        * `result = num1 + num2`
        * `if(num1 > num2) return;`
        * `result = num1 > num2 ? num1 : num2`
    * 一元操作符通常情况下前后不需要有空格，如：
        * `result = num1++`

* 括号：
    * 对于使用括号分割代码块的语言，我们通常有以下要求：
    * 圆括号 `()` 与其它代码块之间通常情况下不存在空格
    * 花括号 `{}` 与其它代码块之间通常情况下存在 `1` 个空格
    * 方括号 `[]` 与其它代码块之间通常情况下不存在空格
    * 如：
      ```TypeScript
      function outNums(nums:number[]):void {
          for(num in nums) {
              console.log(num);
          }
      }
      ```

* 行尾的空字符：在代码行的结尾不应该有任何 `空格` 或者 `制表符` , 即使是空行。

* 嵌套
    * 一般情况下，我们不建议嵌套（如循环，判断等）超过 `4` 层，如：
      ```TypeScript
      function exampleFunc(user:User, data:PlayerData):void {
          if(user.isAdmin()) {
              if(user.isAlive()) {
                  let info:string = "";
                  for(item in data.items) {
                      if(!item.isEmpty()) {
                         info = info + item.name + "\n";
                      }
                  }
                  user.send(info);
              }
          }
      }
      ```
    * 我们可以通过提前返回，函数提取等手段减少代码的嵌套层级，如上面的代码可以修改为：
      ```TypeScript
      function exampleFunc(user:User, data:PlayerData):void {
          if(!user.isAdmin()) return;
          if(!user.isAlive()) return;
          user.send(outItemsName(data.items));
      }

      function outItemsName(items:Item[]):string {
          let info:string = "";
          for(item in data.items) {
              if(item.isEmpty()) continue;
              info = info + item.name + "\n";
          }
          return info;
      }
      ```

## Java

* 命名
    * 类名通常情况下应使用大驼峰命名法，即所有单词首字母大写，如：
        * `User`
        * `PlayerData`
    * 字段通常情况下应使用小驼峰命名法，即第一个单词首字母小写，后续单词首字母大写，如：
        * `address`
        * `phoneNumber`
        * 特殊的，被 `static final` 修饰的字段应使用全大写，以下划线分割的方式命名，如 `GAME_MODE_CREATIVE` ，枚举类的对象应视为被 `static final` 修饰
    * 方法通常情况下应使用使用小驼峰命名法

## C/C++

* 命名
    * 类名、结构体名、 `typedef` 重新定义的类型通常情况下应使用大驼峰命名法
    * 变量、全局变量通常情况下应使用小驼峰命名法
    * 函数通常情况下应使用使用大驼峰命名法
    * 宏常量应使用全大写，以下划线分割的方式命名

## Python

* 命名
    * 类名通常情况下应使用大驼峰命名法
    * 变量、全局变量通常情况下应使用蛇形命名法，即所有单词全小写，以下划线分割，如：
        * `address`
        * `phone_number`
        * 表示常量的不希望被修改的变量应使用全大写，以下划线分割的方式命名
    * 函数通常情况下应使用使用蛇形命名法
