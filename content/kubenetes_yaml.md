

# 1. 개요 

 
 쿠버네티스 배포를 위한 yaml 종류, 문법 사용법 등을 알아보자.

- [Deplyment]


`공식 홈페이지에 있는 Deployment.yaml`

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2 # tells deployment to run 2 pods matching the template
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80

```

* apiVersion  <br> 이 오브젝트를 생성하기 위해 사용하고 있는 쿠버네티스 API 버전이 어떤 것인지

* kind <br> 어떤 종류의 오브젝트를 생성하고자 하는지
* metadata <br> 이름 문자열, UID, 그리고 선택적인 네임스페이스를 포함하여 `오브젝트를 유일하게 구분지어 줄` 데이터
spec - 오브젝트에 대해 어떤 상태를 의도하는지