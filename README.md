# s3-presigned-multipart
This program is to upload big files(>5GB) with presigned and multipart uploading.

## How to use it
Edit run.sh for your environment, and execute run.sh.

```shell
cat run.sh
python3 presigned_multipart_upload.py --bucket 'your-bucket' --key '6g_file' --path '6g_file' --region 'ap-northeast-2'
```

Here is output
```
sh run.sh
-----------
path: 6g_file
byte: 6291456000
15000000 of 6291456000 uploaded (0.238%)
30000000 of 6291456000 uploaded (0.477%)
45000000 of 6291456000 uploaded (0.715%)
60000000 of 6291456000 uploaded (0.954%)
75000000 of 6291456000 uploaded (1.192%)
90000000 of 6291456000 uploaded (1.431%)
105000000 of 6291456000 uploaded (1.669%)
120000000 of 6291456000 uploaded (1.907%)
135000000 of 6291456000 uploaded (2.146%)
150000000 of 6291456000 uploaded (2.384%)
165000000 of 6291456000 uploaded (2.623%)
180000000 of 6291456000 uploaded (2.861%)
195000000 of 6291456000 uploaded (3.099%)
...
...
...
6240000000 of 6291456000 uploaded (99.182%)
6255000000 of 6291456000 uploaded (99.421%)
6270000000 of 6291456000 uploaded (99.659%)
6285000000 of 6291456000 uploaded (99.897%)
6291456000 of 6291456000 uploaded (100.000%)
{'ResponseMetadata': {'RequestId': '3HX7SZ0T4DR4R0YW', 'HostId': 'ROBlrJtg6MEgqrWgRRBezET9p2pK2J5+ZF/rfBtqhUlJlxBlD84xghtV9yVHUn1Gw8n2aOE78ZA=', 'HTTPStatusCode': 200, 'HTTPHeaders': {'x-amz-id-2': 'ROBlrJtg6MEgqrWgRRBezET9p2pK2J5+ZF/rfBtqhUlJlxBlD84xghtV9yVHUn1Gw8n2aOE78ZA=', 'x-amz-request-id': '3HX7SZ0T4DR4R0YW', 'date': 'Fri, 27 Aug 2021 11:07:55 GMT', 'content-type': 'application/xml', 'transfer-encoding': 'chunked', 'server': 'AmazonS3'}, 'RetryAttempts': 0}, 'Location': 'https://your-bucket.s3.ap-northeast-2.amazonaws.com/6g_file', 'Bucket': 'your-bucket', 'Key': '6g_file', 'ETag': '"136fb96c977a305eca0b74d4e84e8adc-420"'}
```

Here is local file info and s3 uploaded object information
```
[s3_presigned_5g]$ aws s3 ls s3://your-bucket/6g_file
2021-08-27 11:06:00 6291456000 6g_file

[s3_presigned_5g]$ ls -l 6g_file2
-rw-rw-r-- 1 ec2-user ec2-user 6291456000 Aug 26 11:08 6g_file2
```

## References
- refered for multipart from: https://gist.github.com/teasherm/bb73f21ed2f3b46bc1c2ca48ec2c1cf5
- refered for presigned from: https://github.com/boto/boto3/issues/2305
