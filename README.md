
<!DOCTYPE html>
<html>
  <head>
		<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
		<script src="../js/jquery-1.7.1.min.js" type="text/javascript"></script>
		<script src="../js/underscore-min.js" type="text/javascript"></script>
		<script src="../js/backbone-min.js" type="text/javascript"></script>
	</head>
	<body>
		<a href="#actions">test actions</a>
		 <a href="#posts/120">Post 120</a>
		<a href="#download/user/images/hey.gif">download gif</a>  
		<a href="#help/1">page</a> 
		<a href="#folder/david/group">folder</a> 
	</body>
	
	<script>
		(function ($){
			var AppRoute = Backbone.Router.extend({
				routes:{
					"posts/:id":"getPost",//传递参数 :表示将#符号后面的字符串当成参数
					":help/:page":         "help",
					 "download/*path":     "download",  //对应的链接为<a href="#download/user/images/hey.gif">download gif</a>  
    				"folder/:name/:mode": "openFolder",
    				"*actions":"defaultRoute", //对应的链接为#actions
				},
				defaultRoute:function(actions){
					console.log("defult");
					alert(actions);
				},
				help:function(cc,page){
					alert(cc+"_"+page);
				},
				openFolder:function(route,action){
					console.log("folder");
					alert(route + "_" + action);
				},
				getPost:function(id){
					alert(id);
				},
				download:function(path){
					 alert(path); // download/user/images/hey.gif   
				},
			});
			var route = new AppRoute;
			Backbone.history.start();
		})(jQuery);
	</script>
</html>


