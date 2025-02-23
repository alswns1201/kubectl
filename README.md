### 쿠버네티스 이해하기 

## 프로젝트구성

## Dokerfile 설정 
- Dokerfile 을 통해서 jar 파일을 doker image로 가공. 
## spring boot 프로젝트 bulid 하기 
- .\gradlew clean build
- docker build -t spring-server .  : spring-server 이미지 생성
  
## 메니페이스트 작성 = 흔히 말하는 yaml 파일 
- Pod 생성을 위한 설정
- apiVersion : v1 => 공식 문서 내용
- spec : Pod의 세부 내용 작성


## ImagePullBackOff 오류 관련 설정 
  ### Always 
- 로컬에서 이미지를 가져오지 않음
- 레지스트리에서 가져옴
  ### IfNotPresent
  - 로컬에서 가져오고 없으면 레지스트리에서 가져옴
  ### Never
  - 로컬에서만 가져옴
  ### 작성안한경우
  - 이미지 태그 버전 latest(default) => Always
  - latest 가 아니면 => IfNotPresent

**imagePullPolicy : Always**


## 디플로이 먼트 
- pod를 3개 띄우기 위해서 메니패스트 에 pod를 3개 설정할것이 아니라 디플로이먼트를 이용하여
  여러개의 Pod를 띄울수 있음
- deployment 에서 레플리카셋을 관리
  **replicas : 3 => 3개의 pod를 띄울 거라고 설정**
- template: metadata: labels: => app: backend-app : app: backend-app 이라는 카테고리를 지정

## 쿠퍼네티스에서의 서비스 - pod에게 균등하게 요청을 분배 해주는 역할
- 로드 벨런서 역할
- 서비스를 통해서 각 pod에게 요청을 보낸다
### spec : type 
- NodePort : 쿠버네티스 내부에서 해당 서비스에 접속하기 위한 포트를 열고 외부에서 접속 가능하게 한다.
- ClusterIp : 쿠버네티스 내부에서만 통신 할수 있는 IP주소를 부여하여 외부에서는 통신 할 수 없다.
- LoadBalancer : 외부의 로드밸런서를 활용(aws의 로드벨런서 등 ) , 외부에서 접속하도록 연결


### 
- kubectl apply -f spirng-deployment.yaml 은 생성 및 변경도 된다.
- 


## 쿠버네티스 명령어
- kubectl cluster-info : 쿠버네티스 동작 확인
- kubectl apply -f .\spring-pod.yaml : yaml 기준 pod 생성
- kubectl get pods : pods 생성 확인
- kubectl delete pod spring-pod : 삭제후 제실행.
- kubectl get deployment : 디플로이먼트 생성
- kubectl get replicaset : 리플리카셋 확인
- 

