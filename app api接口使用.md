####数据库添加数据
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
####android端示例
```java
public class MainActivity extends AppCompatActivity {
    private String TAG = "AA";
    private String url = "http://192.168.1.3/feedback.php";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        RequestQueue requestQueue = Volley.newRequestQueue(getApplicationContext());
        StringRequest stringRequest = new StringRequest(Request.Method.POST, url,
                new Response.Listener<String>() {
                    @Override
                    public void onResponse(String response) {
                        Log.d(TAG, "response -> " + response);
                    }
                }, new Response.ErrorListener() {
            @Override
            public void onErrorResponse(VolleyError error) {
                Log.e(TAG, error.getMessage(), error);
            }
        }) {
            @Override
            protected Map<String, String> getParams() {
                //在这里设置需要post的参数
                Map<String, String> params = new HashMap<>();
                params.put("app", "app名称");
                params.put("msg", "消息内容");
                return params;
            }
        };
        requestQueue.add(stringRequest);
    }
}
```
---
查询数据
```php
<?php
$mysqli = new mysqli("localhost","root","andros230","feedback");
if ($mysqli->connect_error) {  
    die("连接失败: " . $conn->connect_error); 
}  
$mysqli->query("SET NAMES UTF8");
$result = $mysqli->query("select * from feedback");
//或查询指定字段 $result = $mysqli->query("select app from feedback");
$results = array();
while ($row = mysqli_fetch_assoc($result)) {
$results[] = $row;
}
echo json_encode($results,JSON_UNESCAPED_UNICODE);
?>
```
