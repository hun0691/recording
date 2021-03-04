
---
title: "Deplyment"
date: 2021-02-24T17:43:39+09:00
draft: true
---


# Deployment API


- deployment.yaml 샘플코드

``` 
apiVersion: apps/v1
kind: Deployment
metadata:
  # Unique key of the Deployment instance
  name: deployment-example
spec:
  # 3 Pods should exist at all times.
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        # Apply this label to pods and default
        # the Deployment label selector to this value
        app: nginx
    spec:
      containers:
      - name: nginx
        # Run this image
        image: nginx:1.14
```


|Field  |Description|비고|
|:--|:--|:--|
|apiVersion | 버전| 최신 내부값으로  변환해야 한다 . 거부할수 있다 |
|kind| Kind는   이 개체가 나타내는 REST 리소스를 나타내는 문자열 값입니다. | 예시 Deployment|
|metadata (ObjectMeta)| 표준 개체 메타 데이터 | 고유 식별자 정보를 담고 있는 필드| ObjectMeta 로 표현|
|spec (DeplymentSpec)| 원하는 배포 동작 사양| DeplymentSpec 으로 표현|
|status (DeploymentStatus) | 가장최근에 관찰된 배포상태|DeploymentStatus 표현|


## 1. apiVersion 
 * api 문서 버전


## 2. kind 

 * Kind는 이 개체가 나타내는 REST 리소스를 나타내는 문자열 

 ## 3. metadata 

  * 표준 개체 메타 데이터로 ObjectMeta 참고

 ## 4. spec 
 *  원하는 배포 동작 사양	 DeplymentSpec 참고

### 4.1 DeplymentSpec 


| Field | Description |
| ----- | ----------- |
| `minReadySeconds`<br>*integer* | Minimum number of seconds for which a newly created pod should be ready without any of its container crashing, for it to be considered available. Defaults to 0 (pod will be considered available as soon as it is ready) |
| `paused`<br>*boolean* | Indicates that the deployment is paused. |
| `progressDeadlineSeconds`<br>*integer* | The maximum time in seconds for a deployment to make progress before it is considered to be failed. The deployment controller will continue to process failed deployments and a condition with a ProgressDeadlineExceeded reason will be surfaced in the deployment status. Note that progress will not be estimated during the time a deployment is paused. Defaults to 600s. |
| `replicas`<br>*integer* | Number of desired pods. This is a pointer to distinguish between explicit zero and not specified. Defaults to 1. |
| `revisionHistoryLimit`<br>*integer* | The number of old ReplicaSets to retain to allow rollback. This is a pointer to distinguish between explicit zero and not specified. Defaults to 10. |
| `selector`<br>*[LabelSelector](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#labelselector-v1-meta)* | Label selector for pods. Existing ReplicaSets whose pods are selected by this will be the ones affected by this deployment. It must match the pod template's labels. |
| `strategy`<br>*[DeploymentStrategy](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#deploymentstrategy-v1-apps)*<br>**patch strategy**: *retainKeys* | The deployment strategy to use to replace existing pods with new ones. |
| `template`<br>*[PodTemplateSpec](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.20/#podtemplatespec-v1-core)* | Template describes the pods that will be created. |

* replicas - 유지하기 원하는 pod 수 
