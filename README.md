PHP编码规范
===================================
> 文件状态：
> [√] 草稿
> [ ] 正式发布
> [ ] 正在修改	
> 文件标识：	PHP编码规范
> 当前版本：	1.0
> 作    者：	Rich (SevenRich@163.com)
> 完成日期：	2015-10-23
	
1开发工具
-----------------------------------
> Sublime Text 3

2 基本规范
-----------------------------------
（参考ThinkPHP的开发规范，并做适当的修改）
> 1.	类文件都是以 .class.php为后缀（这里是指的ThinkPHP内部使用的类库文件，不代表外部加载的类库文件），使用驼峰法命名，并且首字母大写，例如 DbMysql.class.php； 
> 2.	类的命名空间地址和所在的路径地址一致，例如 Home\Controller\UserController类所在的路径应该是 Application/Home/Controller/UserController.class.php； 
> 3.	确保文件的命名和调用大小写一致，是由于在类Unix系统上面，对大小写是敏感的（而ThinkPHP在调试模式下面，即使在Windows平台也会严格检查大小写）； 
> 4.	类名和文件名一致（包括上面说的大小写一致），例如 UserController类的文件命名是UserController.class.php， InfoModel类的文件名是InfoModel.class.php， 并且不同的类库的类命名有一定的规范； 
> 5.	函数、配置文件等其他类库文件之外的一般是以.php为后缀（第三方引入的不做要求）； 
> 6.	函数的命名使用小写字母和下划线的方式，例如 get_client_ip； 
> 7.	方法的命名使用驼峰法，并且首字母小写或者使用下划线“_”，例如 getUserName，_parseType，通常下划线开头的方法属于私有方法； 
> 8.	属性的命名使用驼峰法，并且首字母小写或者使用下划线“_”，例如 tableName、_instance，通常下划线开头的属性属于私有属性；
> 9.	以双下划线“__”打头的函数或方法作为魔法方法，例如 __call 和 __autoload； 
> 10.	常量以大写字母和下划线命名，例如 HAS_ONE和 MANY_TO_MANY； 
> 11.	配置参数以大写字母和下划线命名，例如HTML_CACHE_ON； 
> 12.	语言变量以大写字母和下划线命名，例如MY_LANG，以下划线打头的语言变量通常用于系统语言变量，例如 _CLASS_NOT_EXIST_； 
> 13.	对变量的命名使用驼峰法，首字母小写 ，例如 infoName； 
> 14.	ThinkPHP的模板文件默认是以.html 为后缀（可以通过配置修改）； 
> 15.	数据表和字段采用小写加下划线方式命名，并注意字段名不要以下划线开头，例如 think_user 表和 user_name字段是正确写法，类似 _username 这样的数据表字段可能会被过滤。



3 概述
-----------------------------------
在符合基本规范的前提下，遵守以下要求。
> 1.	所有PHP文件必须使用 <?php  ?> 长标签, 一定不可使用其它自定义标签; 纯PHP代码文件以 <?php 开头,没有结束标签.
> 2.	所有PHP文件必须且只可使用不带BOM的UTF-8编码。
> 3.	所有PHP文件必须以一个空白行作为结束。
> 4.	代码必须使用4个空格符而不是 tab键 进行缩进。
> 5.	每行的字符数应该软性保持在80个之内， 理论上一定不可多于120个。
> 6.	每个 namespace 命名空间声明语句和 use 声明语句块后面，必须插入一个空白行。
> 7.	类的开始花括号( { )必须写在函数声明后自成一行，结束花括号 ( } ) 也必须写在函数主体后自成一行。
> 8.	方法的开始花括号( { )必须写在函数声明后自成一行，结束花括号( } )也必须写在函数主体后自成一行。
> 9.	类的属性和方法必须添加访问修饰符（private 、protected 以及 public）， abstract 以及 final 必须声明在访问修饰符之前，而 static必须声明在访问修饰符之后。
> 10.	控制结构的关键字后必须要有一个空格符，而调用方法或函数时则一定不能有。
> 11.	控制结构的开始花括号( { )必须写在声明的同一行，而结束花括号( } )必须写在主体后自成一行。
> 12.	控制结构的开始左括号后和结束右括号前，都一定不能有空格符。

### 3.1 例子

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static functionbar()
    {
        // method body
    }
}
```

### 3.2 细节要求
3.2.1 关键词
PHP所有 关键字必须全部小写。
常量 true 、 false 和 null 也必须全部小写。

3.2.2  控制结构
控制结构的基本规范如下：
控制结构关键词后必须有一个空格。
左括号 ( 后一定不能有空格。
右括号 ) 前也一定不能有空格。
右括号 ) 与开始花括号 { 间一定有一个空格。
结构体主体一定要有一次缩进。
结束花括号 } 一定在结构体文体后单独成行。
每个结构体的主体都必须被包含在成对的花括号之中，这能让结构更加话，以及减少加入新行时，出错的可能性。

3.2.2.1 if 、elseif 和 else
标准的 if 结构如下代码所示，留意括号以及花括号的位置，注意 else 和 elseif 都与前面的结束花括号在同一行。

if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}

应该使用关键词 elseif 代替所有 else if ,以使得所有的控制关键字都是单独的一个词。

3.2.2.2 switch 和case
标准的 switch 结构如下代码所示，留意括号、空格以及花括号的位置。 case 语句必须对 switch 进行一次缩进，而 break 语句以及 case 内的其它语句必须相对 case 进行一次缩进。如果存在非空的 case 直穿语句，主体里必须有类似 // no break 的注释。 

<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo '"Second case, which falls through"';
    // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}

3.2.2.3 while 和 do while
一个规范的 while 语句应该如下所示，注意其括号、空格以及花括号的位置。

<?php
while ($expr) {
    // structure body
}

标准的 do while 语句如下所示，同样的，注意其括号、空格以及花括号的位置。

<?php
do {
    // structure body
} while ($expr);

3.2.2.4 for
标准的 for 语句如下所示，注意其括号、空格以及花括号的位置。

<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}

3.2.2.5 foreach
标准的 foreach 语句如下所示，注意其括号、空格以及花括号的位置。

<?php
foreach ($iterable as $key => $value) {
    // foreach body
}

3.2.2.6 try catch
标准的 try catch 语句如下所示，注意其括号、空格以及花括号的位置。

<?php
try {
    // try body
} catch (FirstExceptionType $e) {
   // catch body
} catch (OtherExceptionType $e) {
   // catch body
}

4 代码注释
多行文档注释:  /**   */
普通多行注释:  /*  */
单行注释符号:  //

4.1 文档的注释
PHP文档（demo.php）
/**
 * [doadd description]名字及描述
 * @return [type]类型 [description] 描述
 */

4.2 类文件注释
PHP的类文件(Demo.class.php)
/**
 * 类的简述
 *
 * 类的详细描述
 * @package  sample  简单描述
 * @subpackage  classes  包含类名
 * @author    Rich SevenRich@163.com  作者
 * @version   $Id$  版本
 */

4.3 方法和函数的注释
每个函数，包括对象方法，必须有最少包括下列内容的文档块：
函数的描述;
所有参数;
所有可能的返回值。

/**
 * [doadd description] 描述
 * @param [type] $param [description] 参数类型及描述
 * …
 * @return [type] [description] 返回类型及描述
 */


