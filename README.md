# cloudgo

## 框架使用
### beego

在这里我们使用的是beego框架，以下是获取beego框架的方法
`go get -u github.com/astaxie/beego`

## 内部函数

主要还是用了beego的框架函数来直接实现

```
type MainController struct {
	beego.Controller //beego控制器
}

func (this *MainController) Get() {
	name := this.Ctx.Input.Param(":name")                       //获取路由信息
	this.Ctx.WriteString("Welcome to this page, " + name + "!") //写入
}

func main() {
	port := flag.String("port", "", "port:default is 8080") //传入端口号
	flag.Parse()
	beego.Router("/cloudgo/:name", &MainController{}) //路由设置
	beego.Run(":" + *port)                            //运行
}
```

## 程序运行
- 程序运行
` go run server.go -port 9090`

![](https://github.com/moandy/cloudgo/blob/master/picture/cloudgo1.png?raw=true)

- 浏览器运行

![](https://github.com/moandy/cloudgo/blob/master/picture/cloudgo2.png?raw=true)

- curl 测试

![](https://github.com/moandy/cloudgo/blob/master/picture/cloudgo3.png?raw=true)

- 压力测试

![](https://github.com/moandy/cloudgo/blob/master/picture/cloudgo4.png?raw=true)
![](https://github.com/moandy/cloudgo/blob/master/picture/cloudgo5.png?raw=true)