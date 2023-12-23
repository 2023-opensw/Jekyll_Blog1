# Jekyll Blog

## Getting Started
> Jekyll Build
```
bundle exec jekyll serve
```
http://127.0.0.1:4000 접속 가능

> Kubenetes
```
kubectl get pods -n jekyll-namespace-datacenter
kubectl get service -n jekyll-namespace-datacenter                            
```
NAME                        TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
jekyll-service-datacenter   NodePort   10.110.153.228   <none>        8080:31181/TCP   35m
http://localhost:31181

<br>

---

<br>

## Jekyll.yaml
> Kubernetes Manifest 파일

1. PersistentVolumeClaim (영속적 볼륨 클레임):
- jekyll-site-datacenter이라는 이름의 PersistentVolumeClaim을 정의합니다.
- ReadWriteMany 액세스 모드와 1Gi의 스토리지를 요청합니다.

2. Service (서비스):
- jekyll-service-datacenter라는 이름의 서비스를 정의합니다.
- NodePort 유형으로 지정하여 외부에서 접근할 수 있도록 설정합니다.
- jekyll-pod-datacenter라는 라벨을 가진 Pod를 대상으로 지정합니다.
- 포트 8080을 NodePort 31181로 매핑하며, Pod의 4000 포트로 트래픽을 전달합니다.

3. Pod:
- jekyll-pod-datacenter라는 이름의 Pod를 정의합니다.
- jekyll-pod-datacenter라는 라벨을 포함합니다.
- 이 Pod는 두 가지 컨테이너를 가집니다.
    - 첫 번째는 jekyll-init-datacenter라는 Init 컨테이너로, kodekloud/jekyll 이미지를 사용하여 /site에 새로운 Jekyll 사이트를 만드는 작업을 수행합니다.
    - 두 번째는 jekyll-container-datacenter라는 Jekyll을 실행하는 컨테이너입니다. 이 컨테이너는 kodekloud/jekyll-serve 이미지를 사용하며, /site를 마운트하여 Jekyll 사이트를 호스팅합니다.
