# face.js
使用unicode重新定义emoji表情，以及自定义表情，方便扩展。
主要js代码如下：
var Emoji = {
	reg:/\u0000|\u0001|\u0002|\uffff/g,
	path:'images/',
	png:'.png',
	show:function(text){
		Emoji.emoji(text);
	},
	emoji:function(text){
		var isElement,el,isArr=[];
		if (text.nodeType) {
			el = text;
			text = el.innerHTML;
			isElement = true;
		} 
		var hexToDec = function(str) {
			str=str.replace(/\\/g,"%");
			return unescape(str);
		}

		//unicode字符串转换，否则会当作普通字符处理
		var text = hexToDec(text);
		console.info("text1:",text)
		text = text.replace(Emoji.reg, function(code) {

			console.log("code1:"+code.length);
			return '<img  src="' +Emoji.path  + Emoji.getNum(code) + Emoji.png + '">';
		})
		if (isElement) {
			el.innerHTML = text;
		}
		console.log("what is text?:",text)
		return text;
	},
	_chinishPostFull:function(str){
		
		var arr = [],i=0,l=str.length;
		console.log("chinish:"+ l);
	},
	getNum:function(str){
		console.log("笑脸：" + str)
		 var utfpost = Emoji._coverAs(str);
		var utfto16=utfpost.toString(16)
		console.log("utfpost"+utfpost)
		return utfto16;
	},
	_coverAs:function(str){
		var unicodeCodes = str.charCodeAt(0);
		return unicodeCodes;
	}
}
if (typeof $ !== 'undefined') {
	$.fn.show = function() {
		this.each(function(index, element) {
			Emoji.emoji(element);
		});
	};
}

html代码：
<!doctype html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		body{background:black;}
	</style>
</head>
<body>
		\ua001	\ua002	\ua003	\ua004	\ua005	\ua006	\ua007	\ua008	\ua009	\ua010	\ua011	\ua012	\ua013	\ua014	\ua015	\ua016	\ua017	\ua018	\ua019	\ua020	\ua021	\ua022	\ua023	\ua024	\ua025	\ua026	\ua027	\ua028	\ua029	\ua030	\ua031	\ua032	\ua033	\ua034	\ua035	\ua036	\ua037	\ua038	\ua039	\ua040	\ua041	\ua042	\ua043	\ua044	\ua045	\ua046	\ua047	\ua048	\ua049	\ua050	\ua051	\ua052	\ua053	\ua054	\ua055	\ua056	\ua057	\ua058	\ua059	\ua060	\ua061	\ua062	\ua063	\ua064	\ua065	\ua066	\ua067	\ua068	\ua069	\ua070	\ua071	\ua072	\ua073	\ua074	\ua075	\ua076	\ua077	\ua078	\ua079	\ua080	\ua081	\ua082	\ua083	\ua084	\ua085	\ua086	\ua087	\ua088	\ua089	\ua090	\ua091	\ua092	\ua093	\ua094	\ua095	\ua096	\ua097	\ua098	\ua099	\ua100	\ua101	\ua102	\ua103	\ua104	\ua105	\ua106	\ua107	\ua108	\ua109	\ua110	\ua111	\ua112	\ua113	\ua114	\ua115	\ua116	\ua117	\ua118	\ua119	\ua120


</body>
</html>
<script src="jquery-2.1.4.min.js"></script>
<script src="js.js"></script>
<script>
$("body").show();
</script>

图片命名规则：
如：\ua001，图片名为a001.gif   \ua020，图片名为a020.gif 即可
