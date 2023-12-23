# Jekyll Blog

## ref.
- Theme : [plainwhite-jekyll](https://github.com/samarsault/plainwhite-jekyll)

<br>

---

<br>

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
|NAME|TYPE|CLUSTER-IP|EXTERNAL-IP|PORT(S)|AGE|
|---|---|---|---|---|---|
|jekyll-service-datacenter|NodePort|10.110.153.228|< none >|8080:31181/TCP|35m|

http://localhost:31181 접속 가능

<br>

---

<br>

## k8s/Jekyll.yaml
> Kubernetes Manifest 파일

**1. PersistentVolumeClaim (퍼시스턴트 볼륨):**
- jekyll-site-datacenter 이름의 PersistentVolumeClaim 정의
- ReadWriteMany 액세스 모드와 1Gi 스토리지 요청

**2. Service :**
- jekyll-service-datacenter 이름의 서비스 정의
- NodePort 유형으로 지정하여 외부에서 접근할 수 있도록 설정
- jekyll-pod-datacenter 라벨을 가진 Pod를 대상으로 지정
- 포트 8080을 NodePort `31181`로 매핑, Pod의 `4000` 포트로 트래픽 전달

**3. Pod :**
- jekyll-pod-datacenter 이름의 Pod 정의
- jekyll-pod-datacenter 라벨 포함
- 두 가지 컨테이너
    - 1. jekyll-init-datacenter (Init 컨테이너)
        kodekloud/jekyll 이미지를 사용하여 `/site`에 새로운 Jekyll 사이트 생성 작업 수행
    - 2. jekyll-container-datacenter (Jekyll 실행 컨테이너) 
        kodekloud/jekyll-serve 이미지 사용, `/site`를 마운트하여 Jekyll 사이트 호스팅
