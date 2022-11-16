## 点击复制文本

//复制文本

navigator.clipboard.writeText(/要复制的内容/)

//读取文本

navigator.clipboard.readText().then((text)=>{

​	//这里的text就是当前剪切板的内容

})

## 导出execl

let execlContent="姓名，电话" //首先我们先写一个标题用逗号隔开

然后我们可以去循环我们请求回来的数据去拼接我们的execl

for (let i=0;i<data.length;i++){

​	execlContent+='/n掌声,dwadaw' //记得在每一行前面都加上换行符才可以被区分

}

let blob=new Blob([execlContent],{type:"application/vnd.ms-excel"})//这里我们将其内容转换为原生的二进制

let blob=new Blob([string.fromCharCode('0xFEFF'),blob],{type:"application/vnd.ms-excel"})//我们在这里

let link =document.createElement('a')

document.body.appendChild(link)

link.href=URL.createObjectUrl(blob)

//我们创建一个a标签然后将其添加到页面上，然后创建它的href 用我们的url的createObjectUrl方法将其blob对象变成我们的数据链接

link.download='文件名'	//这里配置我们的文件名

link.click() //最后我们触发a标签的点击事件下载

document.body.removeChild(link)//销毁我们的a标签dom

URL.revokeObjectUrl(link.href)//然后销毁我们的临时数据链接

