# Protocol-Buffer-
本文记录一下在android上使用protocol buffer 作为通讯数据格式的记录。IDE eclipse <br/>
[Google 源码 github ](https://github.com/google/protobuf)

### protocol buffer 主要优势

1. 序列化/反序列化时效快
2. 体积小(数量级的变化)

### protocol buffer 主要劣势
1. 可读性差(序列化之后变成了字符串，完全不可读)
2. 需要第三方参与编译和自动生成(协议结构需改变时，需重新生成)
3. 库文件不得不包含，很多高级功能其实并用不到，xml & json 可以自己解析，支持本工程即可

## protocol buffer 应用
环境说明 <br/>
1. for android <br/>
2. on mac (pro , OS X) <br/>
3. eclipse <br/>

## 步骤
1. mac 安装 brew ( homebrew ) <br/>
    [brew 官网](http://brew.sh/) <br/>
    现行安装命令 : /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" (需 ruby 环境)<br/>
2. brew 安装 protobuf (三个命令均需执行)
  brew install automake
  brew install libtool
  brew install protobuf
3. 安装完毕后验证
  protoc --version
4. 编辑.proto文件
5. 使用命令行自动生成.java 文件
  protoc ./filename.proto --java_out=./
6.该Java文件copy至工程中，手动修改包名 link warming( if necessary)


#### 注意
1. Android工程中引用的jar包版本需与mac中protoc 版本匹配，如执行 protoc --version 显示 2.6.1 则在工程中需引用v2.6.1jar包(否则可能会引起类库不匹配，无法编译)
2. 包名可修改，filename.proto最好放置工程src目录下，如此就可方便在命令行下直接将.java文件输出到对应的包下<br/>
  不放置也可，生成.java文件后，copy至对应的包名再修改.java文件的包名即可
3. 序列化后的数据可以直接使用messageName.toByteArray()得到




