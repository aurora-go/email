# aurora-email

aurora-email 实现简单的 text , html , file 附件的消息发送

使用demo

```go
func TestMaintest(t *testing.T) {
	email := NewClient("xxxxx@qq.com", "xxxasaxxasx", "smtp.qq.com")
	email.Name("aurora-email Manager")
	email.Subject("测试邮件")
	email.Text("test 普通文本消息")
	email.Html(`<!DOCTYPE html>
	<html lang="en">
		<head>
	     <meta http-equiv="Content-Type" content="text/html;charset=utf-8" />
		   <title>Title</title>
		</head>
		<body>
			<p style="font-size:30px;color:orange">测试HTML 信息</p>
		</body>
	</html>`)

	//添加一个pdf
	file, err := os.ReadFile("1111.pdf")
	if err != nil {
		fmt.Println(err.Error())
		return
	}
	email.File("test.pdf", file)

	//添加一首音乐
	file, err = os.ReadFile("Hillsong Young & Free - Wake (Studio) [mqms2].flac")
	if err != nil {
		fmt.Println(err.Error())
		return
	}
	email.File("Hillsong Young & Free - Wake (Studio) [mqms2].flac", file)

	_, err = email.SendEmail("asd.asdas@xxxx.com", "asdawq@qq.com")
	if err != nil {
		fmt.Println(err.Error())
		return
	}
}

```

