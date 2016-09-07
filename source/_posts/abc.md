---
title: 测试文章
date: 2016-09-02 23:01:19
comments: false
---

## Quick Start

### Create a new post

``` 
package main;

public class HttpUtil {

	public static String doPost(String url,Map<String,String> map) throws Exception {
		String uriAPI = url;// Post方式没有参数在这里
		String result = "";
		HttpPost httpRequst = new HttpPost(uriAPI);// 创建HttpPost对象
		List params = new ArrayList();
		
		Set<Entry<String, String>> entrys=map.entrySet();
		Iterator<Entry<String, String>> it=entrys.iterator();
		while(it.hasNext()){
			Entry<String, String> e=it.next();
			params.add(new BasicNameValuePair(e.getKey(),e.getValue()));
		}
		
			httpRequst.setEntity(new UrlEncodedFormEntity(params, HTTP.UTF_8));
			HttpResponse httpResponse = new DefaultHttpClient()
					.execute(httpRequst);
			if (httpResponse.getStatusLine().getStatusCode() == 200) {
				HttpEntity httpEntity = httpResponse.getEntity();
				result = EntityUtils.toString(httpEntity);// 取出应答字符串
			}
		
		return result;
	}

}


```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` 
$ hexo server
```

![img](/img/001.jpg)

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` 
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` 
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)
