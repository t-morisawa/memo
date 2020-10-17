# Amazon Rekognition

https://docs.aws.amazon.com/ja_jp/rekognition/latest/

## 顔認識

 - DetectFaces API
   - https://docs.aws.amazon.com/ja_jp/rekognition/latest/dg/API_DetectFaces.html
 - リクエストではBase64エンコードされた画像かS3オブジェクトの参照を渡す
 
```
{
   "Attributes": [ "string" ],
   "Image": { 
      "Bytes": blob,
      "S3Object": { 
         "Bucket": "string",
         "Name": "string",
         "Version": "string"
      }
   }
}
```
