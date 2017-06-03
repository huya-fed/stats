# Stats

---

性能监视器

---


## 提供了4种的性能监控


FPS监视器 ： 上一秒的帧数，越大越好，一般为60左右

MS监视器 ：  表示渲染一帧需要的毫秒数，越小越好。

MB监视器 ： 占用内存多少M字节。启动谷歌浏览器时，使用

	--enable-precise-memory-info  

	windows具体做法为：
	
	1.在电脑上新建一个目录，例如：C:\MyChromeDevUserData
	
	2.在属性页面中的目标输入框里加上 --enable-precise-memory-info --user-data-dir=C:\MyChromeDevUserData
	
	3.点击应用和确定后关闭属性页面，并打开chrome浏览器。

CUSTOM监视器 ： 支持用户自定义的panel


## 使用Stats

	var stats = new Stats();
	stats.showPanel( 1 ); // 0: fps, 1: ms, 2: mb, 3+: custom
	document.body.appendChild( stats.dom );
	
	function animate() {
	    stats.begin();
	    // monitored code goes here
	    stats.end();
	    requestAnimationFrame( animate );
	}
	
	requestAnimationFrame( animate );



## 自定义监视器

    监听dom的数量变化,例子 

	https://hilongjw.github.io/vue-recyclerview/


	var i = new window.Stats,
		s = new window.Stats.Panel("DOM Nodes", "#0ff", "#002");
	i.addPanel(s), i.showPanel(3), 
	s.dom.style.display = "", 
	i.dom.style.top = "50px", 
	document.body.appendChild(i.dom);
	
	setTimeout(function t() {
		requestAnimationFrame(function() {
			s.update(o(document.body), 1500), setTimeout(t, 500)
		})
	}, 500)




## 直接引用方式

	(function() {
		var script = document.createElement('script');
		script.onload = function() {
			var stats = new Stats();
			document.body.appendChild(stats.dom);
			requestAnimationFrame(function loop() {
				stats.update();
				requestAnimationFrame(loop)
			});
		};
		script.src = '//rawgit.com/mrdoob/stats.js/master/build/stats.min.js';
		document.head.appendChild(script);
	})()




## 参考

http://www.cnblogs.com/cshi/p/5660039.html

https://github.com/mrdoob/stats.js