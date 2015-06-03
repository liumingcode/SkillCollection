
1、获取数组里面的最大值和最小值(其中numbers为对应的数组)
console.log(Math.max.apply(Math,numbers));
console.log(Math.min.apply(Math,numbers));

2、搜索文字高亮
$("#replace").on("click",function(){
	var content = $("div[class=article]").text().trim(); //文章内容
	var key = $("input[type=text]").val().trim();//关键字
	var reg = new RegExp(key,"g");
	if(reg.test(content)){
		var item = content.replace(reg,function(t){
			return "<span class=\"addColor\">"+t+"</span>";//添加样式
		});
		$("div[class=article]").html(item).show();
	}else{
	  //在不匹配的情况之下清除以前的样式			
	  $("div[class=article]").find("span[class=addColor]").removeClass("addColor");
	 }
});

3、扩展数组的删除方法
Array.remove = function(array,form,to){
	var rest = array.slice((to || form) + 1 || array.length);
	array.length = form < 0 ? array.length + form : form;
	return array.push.apply(array,rest);
}
