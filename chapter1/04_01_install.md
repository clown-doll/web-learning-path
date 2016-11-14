# 安装

## 安装Ruby

Sass 依赖于 Ruby 环境，所以安装 Sass 前必须先安装 Ruby。（注意：mac下自带Ruby无需在安装Ruby）

在安装过程中，建议将其安装在 C 盘下，并且选择第二个选项，添加环境变量，如下图所示：

![](/assets/install-ruby-min.jpg)

安装完成后可以测试安装有没有成功，运行 CMD 输入以下命令：

```
ruby -v
```

如果安装成功，会打印出对应的版本号等信息：

```
ruby 2.2.3p173 (2015-08-18 revision 51636) [i386-mingw32]
```

Ruby 安装完成后，在开始菜单中找到新安装的 Ruby，并启动 Ruby 的 Command 控制面板，如下图所示：

![](/assets/ruby-command-min.jpg)

## 安装sass

在完成 Ruby 的安装后，就可以开始安装 Sass 了。

### 1. 通过命令安装sass

在 Ruby 的 Command 控制面板中输入：

```
gem install sass
```

按回车键确认，等待一段时间就会提示你sass安装成功。

由于国内的网络限制，可能会导致安装不能成功，这种情况可以参考下面的方法来安装。

### 2. 本地安装 Sass

由于网络的限制，我们可以下载 Sass 安装包到本地安装。具体操作步骤如下： 

到 Rubygems 网站上将 Sass 的安装包 下载下来，然后在命令终端输入：

```
gem install <把下载的安装包拖到这里>
```

直接回车即可安装成功。

### 3. 淘宝 RubyGems 镜像安装 Sass

除了下载 Sass 安装包到本地安装之外，碰到网络原因无法安装时还可以使用淘宝 RubyGems 镜像安装 Sass。具体步骤如下：

**第一步：移除默认的源**

```
gem sources --remove https://rubygems.org/
```

**第二步：指定淘宝的源**

```
gem sources -a https://ruby.taobao.org/
```

**第三步：查看指定的源是不是淘宝源**

```
gem sources -l
```

返回结果如下：

```
*** CURRENT SOURCES ***
https://ruby.taobao.org
请确保只有 ruby.taobao.org。如果无误之后，执行下面的命令：
gem install sass
```

安装完成之后，你可以通过运行下面的命令来确认应用已经正确地安装到了电脑中：

```
sass -v
```

如果安装成功，会打印出对应的版本号等信息：

```
Sass 3.3.14 (Maptastic Maple)
```

