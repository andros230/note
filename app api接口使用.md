```php
<?php
$app = $_POST['app'];
$msg = $_POST['msg'];

//连接数据库
$mysqli = new mysqli("localhost","root","andros230","feedback");

if ($mysqli->connect_error) {  
    die("连接失败: " . $conn->connect_error);
}  
$mysqli->query("SET NAMES UTF8");
$insert_row = $mysqli->query("INSERT INTO feedback (app,msg) VALUES('$app','$msg')");

if($insert_row){
	//保存成功
	$arr = array(
		'code'=>200,
		'msg'=>"Success"
	);
	echo json_encode($arr,JSON_UNESCAPED_UNICODE);
	
}else{
	//保存失败
	$error = array(
		'code'=>201,
		'msg'=>"error"
	);
	echo json_encode($error,JSON_UNESCAPED_UNICODE);
}
?>
```
