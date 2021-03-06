## 1. API Description

This API (UnassignPrivateIpAddresses) is used to return the private IP of ENI.
Domain for API request: <font style="color:red">vpc.api.qcloud.com</font>

If an auxiliary private IP on the ENI is returned, the API will automatically dissociate it from the elastic public IP. The primary auxiliary private IP on the ENI cannot be returned.

## 2. Input Parameters
The following request parameter list only provides API request parameters. Common request parameters need to be added when the API is called. For more information, refer to <a href="/doc/api/372/4153" title="Common request parameters">Common Request Parameters</a>. The Action field for this API is UnassignPrivateIpAddresses.

| Parameter Name | Required  | Type | Description |
|---------|---------|---------|---------|
| vpcId | Yes | String | Virtual private cloud ID of ENI, for example: vpc-7t9nf3pu |
| networkInterfaceId | Yes | String | ENI ID, for example: eni-m6dyj72l |
| privateIpAddress.n | Yes | Array | The auxiliary private IP address array to be returned, for example: privateIpAddress.0=10.0.0.2 |

## 3. Output Parameters

| Parameter Name | Type | Description |
|---------|---------|---------|
| code | Int | Error code. 0:  Succeeded, other values:  Failed |
| message | String | Error message |
| taskId | Int | Task ID. The operation result can be queried with taskId. For more information, refer to <a href="https://cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e4%bb%bb%e5%8a%a1%e6%89%a7%e8%a1%8c%e7%bb%93%e6%9e%9c%e6%8e%a5%e5%8f%a3">API for Querying Task Execution Result</a>.  |

## 4. Error Codes
The following list only provides the business logic error codes for this API. For additional common error codes, refer to <a href="https://cloud.tencent.com/doc/api/245/4924" title="VPC Error Codes">VPC Error Codes</a>.

| Error Code | Description |
|---------|---------|
| InvalidVpc.NotFound | VPC does not exist. Please check the information you entered. You can query the VPC via the <a href="http://cloud.tencent.com/doc/api/245/%E6%9F%A5%E8%AF%A2%E7%A7%81%E6%9C%89%E7%BD%91%E7%BB%9C%E5%88%97%E8%A1%A8" title="DescribeVpcEx">DescribeVpcEx</a> API |
| InvalidNetworkInterface.NotFound |ENI does not exist. Please check the information you entered. You can query the ENI via the <a href="https://cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e5%bc%b9%e6%80%a7%e7%bd%91%e5%8d%a1%e4%bf%a1%e6%81%af?viewType=preview" title="DescribeNetworkInterfaces">DescribeNetworkInterfaces</a> API |
| InvalidPrivateip.IsPrimary | The primary IP cannot be unbound |

## 5. Example
Input
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=UnassignPrivateIpAddresses
&<<a href="https://cloud.tencent.com/doc/api/229/6976">Common request parameters</a>>
&vpcId=vpc-7t9nf3pu
&networkInterfaceId=eni-m6dyj72l
&privateIpAddress.0=10.0.0.2
</pre>
Output
```
{
    "code":"0",
    "message":"",
    "taskId":16284
}
```


