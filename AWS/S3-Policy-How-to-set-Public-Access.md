기본적으로 새 버킷, 액세스 포인트 및 객체는 퍼블릭 액세스를 허용하지 않아, 퍼블릭 액세스가 필요하다면 버킷 정책, 액세스 포인트 정책, 객체 권한 등을 수정하여 허용하게 할 수 있다.

## 1. S3 버킷 생성 시 Public Access 차단 체크 해제

![image](https://user-images.githubusercontent.com/68765200/226365766-8ea07339-b9af-4be2-b81f-94ab50e3a129.png)

이렇게만 설정해서는 바로 액세스 퍼블릭으로 바꿀 수 없다. 정책이 필요하다.

## 2. 버킷 정책 수정

- **(중요)** 복사한 ARN 주소를 다음과 같이 수정 `arn:aws:s3:::/{$PATH}/*`
    - 수정하지 않고 그대로 ARN 주소를 Resource에 작성하면 Action does not apply to any resource(s) in statement 에러가 뜬다 - 와일드카드(*) 혹은 특정 리소스를 명시해주자. 버킷 하위의 모든 객체에 적용하려면 /* 를 사용하면 된다.
        
        참고: [정책 JSON 에서 ‘resource’ 요소의 작성 방법과 예시(공식문서)](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_resource.html)
        
- [정책 생성기](https://awspolicygen.s3.amazonaws.com/policygen.html)를 이용해 Json 생성 (아래는 옵션 입력 및 선택 내용)
    - Principal: *
    - AWS Service: S3
    - Action: GetObject
    - ARN: 앞서 편집한 ARN 주소 + /*
    
- [Generate Policy] 선택 후 정책을 복사 → [버킷 개요]의 [권한] -> [버킷 정책] -> [편집]에 붙여넣기

```python
{
    "Version": "2012-10-17",
    "Id": "Policy1678019929923",
    "Statement": [
        {
            "Sid": "Stmt1678019691465",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:DeleteObject",
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": "arn:aws:s3:::bungae-bucket/*"
        }
    ]
}
```

+ CORS 설정

웹의 경우 이를 설정해주어야 에러없이 파일을 불러올 수 있다고 한다.
```
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "HEAD",
            "GET",
            "PUT",
            "POST",
            "DELETE"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": []
    }
]
```
