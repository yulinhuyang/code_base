## prefix

1 Course overview + the shell

2 Shell Tools and Scripting

3 Editors (Vim)

4 Data Wrangling

5 Command-line Environment

6 Version Control (Git)

7 Debugging and Profiling

8 Metaprogramming

9 Security and Cryptography

10 Potpourri

11 Q&A


## Course overview + the shell

### 使用 shell

date: 日期时间

echo：将该参数打印出来

shell： 一个编程环境，所以它具备变量、条件、循环和函数。当你在 shell 中执行命令时，您实际上是在执行一段 shell 可以解释执行的简短代码

echo $PATH  查看环境变量

which ： 确定某个程序名代表的是哪个具体的程序
 
 
 ### 在shell中导航
 
/ 代表的是系统的根目录

pwd  当前目录  

cd  切换目录，. 表示的是当前目录，而 .. 表示上级目录

ls -l 查看
 
 mv（用于重命名或移动文件）、 cp（拷贝文件）以及 mkdir（新建文件夹）
 
### 在程序间创建连接
 
流重定向： < file 和 > file 

    cat hello.txt
    cat < hello.txt > hello2.txt
    
>> 来向一个文件追加内容

管道： | 操作符 将一个程序的输出和另外一个程序的输入连接起来
  
    ls -l / | tail -n1

    echo 3 | sudo tee brightness

## Shell 工具和脚本

### Shell 脚本

shell脚本针对shell所从事的相关工作进行来优化

bash中为变量赋值的语法是foo=bar，访问变量中存储的数值，其语法为 $foo

Bash中的字符串通过' 和 "分隔符来定义，以'定义的字符串为原义字符串，其中的变量不会被转义，而 "定义的字符串会将变量值进行替换

    foo=bar
    echo "$foo"
    # 打印 bar
    echo '$foo'
    # 打印 $foo

bash也支持if, case, while 和 for 这些控制流关键字, bash 也支持函数

bash使用了很多特殊的变量来表示参数、错误代码和相关变量

    $0 - 脚本名
    $1 到 $9 - 脚本的参数。 $1 是第一个参数，依此类推。
    $@ - 所有参数
    $# - 参数个数
    $? - 前一个命令的返回值

退出码可以搭配&& (与操作符) 和 || (或操作符)使用，用来进行条件判断，决定是否执行其他程序。同一行的多个命令可以用 

$( CMD ) ：这样的方式来执行CMD 这个命令时，然后它的输出结果会替换掉 $( CMD )

    #!/bin/bash

    echo "Starting program at $(date)" # date会被替换成日期和时间

    echo "Running program $0 with $# arguments with pid $$"

    for file in $@; do
        grep foobar $file > /dev/null 2> /dev/null
        # 如果模式没有找到，则grep退出状态为 1
        # 我们将标准输出流和标准错误流重定向到Null，因为我们并不关心这些信息
        if [[ $? -ne 0 ]]; then
            echo "File $file does not have any foobar, adding one"
            echo "# foobar" >> "$file"
        fi
    done
    
**通配符：**

? 和 * 来匹配一个或任意个字符

花括号{} - 当你有一系列的指令，其中包含一段公共子串时，可以用花括号来自动展开这些命令    
    
      convert image.{png,jpg}
      # 会展开为
      convert image.png image.jpg

      cp /path/to/project/{foo,bar,baz}.sh /newpath
      # 会展开为
      cp /path/to/project/foo.sh /path/to/project/bar.sh /path/to/project/baz.sh /newpath

      # 也可以结合通配使用
      mv *{.py,.sh} folder
      # 会移动所有 *.py 和 *.sh 文件

      mkdir foo bar

      # 下面命令会创建foo/a, foo/b, ... foo/h, bar/a, bar/b, ... bar/h这些文件
      touch {foo,bar}/{a..h}
      touch foo/x bar/y
      # 显示foo和bar文件的不同
      diff <(ls foo) <(ls bar)
      # 输出
      # < x
      # ---
      # > y

### Shell 工具

man 命令：提供了命令的用户手册

TLDR pages ：搜索命令手册

tar 、 ffmpeg： https://tldr.ostera.io/ffmpeg

**查找文件：**

find命令会递归地搜索符合条件的文件

    # 查找所有名称为src的文件夹
    find . -name src -type d
    # 查找所有文件夹路径中包含test的python文件
    find . -path '**/test/**/*.py' -type f
    # 查找前一天修改的所有文件
    find . -mtime -1
    # 查找所有大小在500k至10M的tar.gz文件
    find . -size +500k -size -10M -name '*.tar.gz'

fd: 作为find的替代品

https://github.com/sharkdp/fd

locate: 只能通过文件名。

对比： https://unix.stackexchange.com/questions/60205/locate-vs-find-usage-pros-and-cons-of-each-other

**查找代码**

grep

-C ：获取查找结果的上下文（Context）；

-v 将对结果进行反选（Invert），也就是输出不匹配的结果

-R 会递归地进入子目录并搜索所有的文本文件

替代品：

ack

ag： https://github.com/ggreer/the_silver_searcher

ripgrep (rg)：https://github.com/BurntSushi/ripgrep

    # 查找所有使用了 requests 库的文件
    rg -t py 'import requests'
    # 查找所有没有写 shebang 的文件（包含隐藏文件）
    rg -u --files-without-match "^#!"
    # 查找所有的foo字符串，并打印其之后的5行
    rg foo -A 5
    # 打印匹配的统计信息（匹配的行和文件的数量）
    rg --stats PATTERN
    
**查找 shell 命令**

history 命令允许您以程序员的方式来访问shell中输入的历史命令

     history | grep find 会打印包含find子串的命令

Ctrl+R ： 对命令历史记录进行回溯搜索。敲 Ctrl+R 后您可以输入子串来进行匹配
    
zsh: https://github.com/zsh-users/zsh-history-substring-search

fzf: 通用对模糊查找工具，https://github.com/junegunn/fzf/wiki/Configuring-shell-key-bindings#ctrl-r  可以对历史命令进行模糊查找并将结果以赏心悦目的格式输出

基于历史的自动补全： zsh： https://github.com/zsh-users/zsh-autosuggestions

您在命令的开头加上一个空格，它就不会被加进shell记录中，通过编辑。bash_history或 .zhistory移除那一项

**文件夹导航**

目录切换： 设置alias，使用 ln -s创建符号连接

fasd: https://github.com/clvv/fasd, 查找最常用和/或最近使用的文件和目录。Fasd 基于 frecency对文件和文件排序，也就是说它会同时针对频率（frequency ）和时效（ recency）进行排序

自动跳转 （autojump）:对于经常访问的目录，在目录名子串前加入一个命令 z 就可以快速切换命令到该目录

其他复杂工具：  tree, broot 或更加完整的文件管理器，例如 nnn 或 ranger


### 数据整理

日志处理：

ssh myserver journalctl | grep sshd

改进： ssh myserver 'journalctl | grep sshd | grep "Disconnected from"' | less

我们先在远端机器上过滤文本内容，然后再将结果传输到本机。 less 为我们创建来一个文件分页器，使我们可以通过翻页的方式浏览较长的文本

甚至可以将当前过滤出的日志保存到文件中

   $ ssh myserver 'journalctl | grep sshd | grep "Disconnected from"' > ssh.log
   $ less ssh.log

**sed**

sed  基于文本编辑器ed构建的”流编辑器”

可以利用一些简短的命令来修改文件，而不是直接操作文件的内容，最常用的是 s，即替换命令

    ssh myserver journalctl
     | grep sshd
     | grep "Disconnected from"
     | sed 's/.*Disconnected from //'

s 命令的语法：s/REGEX/SUBSTITUTION/, 其中 REGEX 部分是我们需要使用的正则表达式，而 SUBSTITUTION 是用于替换匹配结果的文本

**正则表达式**

常见的模式有：

    . 除空格之外的”任意单个字符”
    * 匹配前面字符零次或多次
    + 匹配前面字符一次或多次
    [abc] 匹配 a, b 和 c 中的任意一个
    (RX1|RX2) 任何能够匹配RX1 或 RX2的结果
    ^ 行首
    $ 行尾

* 和 + 在默认情况下是贪婪模式，会尽可能多的匹配文本。可以给 * 或 + 增加一个? 后缀使其变成非贪婪模式。

perl 的命令行模式：

    perl -pe 's/.*?Disconnected from //'


正则表达式在线调试工具regex debugger： https://regex101.com/r/qqbZqh/2

    | sed -E 's/.*Disconnected from (invalid |authenticating )?user (.*) [^ ]+ port [0-9]+( \[preauth\])?$/\2/'

捕获组（capture groups）： 被圆括号内的正则表达式匹配到的文本，都会被存入一系列以编号区分的捕获组中。捕获组的内容可以在替换字符串时使用

**回到数据整理**

sed  文本注入：(使用 i 命令)，打印特定的行 (使用 p命令)

sort 会对其输入数据进行排序。sort -n 会按照数字顺序对输入进行排序.  -k1,1 则表示“仅基于以空格分割的第一列进行排序”。,n 部分表示“仅排序到第n个部分”

uniq -c 会把连续出现的行折叠为一行并使用出现次数作为前缀

登陆次数最少的用户: 可以使用 head 来代替tail。或者使用sort -r来进行倒序排序

    ssh myserver journalctl
     | grep sshd
     | grep "Disconnected from"
     | sed -E 's/.*Disconnected from (invalid |authenticating )?user (.*) [^ ]+ port [0-9]+( \[preauth\])?$/\2/'
     | sort | uniq -c
     | sort -nk1,1 | tail -n10
     | awk '{print $2}' | paste -sd,

paste命令来合并行(-s)，并指定一个分隔符进行分割 (-d)

**awk – 另外一种编辑器**

awk 程序接受一个模式串（可选），以及一个代码块，指定当模式匹配时应该做何种操作. 在代码块中，$0 表示整行的内容，$1 到 $n 为一行中的 n 个区域，区域的分割基于 awk 的域分隔符.

    | awk '$1 == 1 && $2 ~ /^c[^ ]*e$/ { print $2 }' | wc -l

第一部分需要等于1, 其第二部分必须满足给定的一个正则表达式, 代码块中的内容则表示打印用户名。然后我们使用 wc -l 统计输出结果的行数

    BEGIN { rows = 0 }
    $1 == 1 && $2 ~ /^c[^ ]*e$/ { rows += $1 }
    END { print rows }

**分析数据**

  gnuplot: 绘制一些简单的图表

  xargs:  给命令传递参数的一个过滤器. 利用数据整理技术从一长串列表里找出你所需要安装或移除的东西
  
    rustup toolchain list | grep nightly | grep -vE "nightly-x86" | sed 's/-x86.*//' | xargs rustup toolchain uninstall

 整理二进制数据: 用 ffmpeg 从相机中捕获一张图片，将其转换成灰度图后通过SSH将压缩后的文件发送到远端服务器，并在那里解压、存档并显示。
 
    ffmpeg -loglevel panic -i /dev/video0 -frames 1 -f image2 -
    | convert - -colorspace gray -
    | gzip
    | ssh mymachine 'gzip -d | tee copy.jpg | env DISPLAY=:0 feh -'
 
 
    
    
 

