+++
title = "home"
date = 2018-07-05T04:20:00Z
weight = 1
alwaysopen = true
+++

# Cloud Z Composer
--- 
Cloud Z Composer는 IT 자동화의 확장, 복잡한 배치 관리 및 생산성 향상을 지원합니다. 앱 배포에서 다중 계층 조정에 이르기까지 제어, 보안 및 위임 기능을 추가하여 엔터프라이즈 자동화를 지원합니다. 시각적 대시 보드, 역할 기반 액세스 제어, 작업 스케줄링, 통합 알림 및 그래픽 인벤토리 관리로 IT 인프라를 중앙 집중화하고 제어하십시오.

> Cloud Z Composer의 REST API 및 CLI를 사용하면 기존 도구 및 프로세스에 Cloud Z Composer를 쉽게 사용 할 수 있습니다.

## Dash Board
---
### Dash Board란?
Cloud Z Composer Dash Board는 각종 배포 자동화 환경에서 진행되는 모든 작업에 대한 디스플레이를 제공합니다.


### 출력 대상

출력 대상은 다음과 같은 항목들이 있습니다.

- Host 및 Inventory
- 최근 작업 활동
- 최근 작업 실행의 Snapshot
- 작업 상태
- 특정 작업 및 시간 범위의 데이터를 그래프화

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/1dashboard.png)

## 실시간 작업 상태 업데이트
---
Cloud Z Composer 내에서 Playbook은 실시간 스트림 형태로 실행됩니다. Cloud Z Composer는 인프라 전반에서 자동화되므로 각 호스트별로 완전히 분리되고 성공 또는 실패가 출력과 함께 완료됩니다.

자동화 상태와 대기열에 있는 다음 사항을 쉽게 확인할 수 있습니다.

- 소스 제어 업데이트
- 클라우드 Inventory 갱신
- 다른 유형의 작업을 공통 작업 목록에 표시

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/2job_result.png)

## Multi Playbook 워크플로우
---
Cloud Z Composer의 Multi Playbook 워크플로우는 다른 인벤토리를 사용하든, 다른 사용자로 실행하든, 한 번에 실행하든, 다른 자격 증명을 활용하든 상관없이 원하는 수의 Playbook을 연결할 수 있습니다.

Cloud Z Composer는 많은 복잡한 작업을 처리하는 프로비저닝 워크플로우를 구축할 수 있습니다.

- 시스템 프로비저닝
- 기본 시스템 구성 적용
- 애플리케이션 배포

Work Flow는 서로 다른 팀에서 관리하는 다양한 Playbook으로 제공됩니다.

- 애플리케이션을 빌드
- 테스트 환경에 배포
- 테스트 실행
- 테스트 결과에 따라 애플리케이션을 자동으로 구분하는 CI/CD 테스트 워크플로우를 구축

>이전 워크플로우 Playbook의 성공 또는 실패 시 실행할 다른 Playbook을 설정합니다.

> Cloud Z Composer의 직관적인 워크플로우 편집기를 사용하여 복잡한 프로세스를 쉽게 모델링할 수 있습니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/3workflow.png)

## Role based 접근 관리
---
Cloud Z Composer를 사용하면 모든 자동화 활동이 안전하게 기록됩니다.

- 누가 실행했는지
- 어떻게 정의했는지
- 어떤 Job이 실행했는지

> 모두 안전하게 저장 및 볼 수 있으며, API를 통해 내용을 Export 할수 있습니다.

활동 스트림은 Cloud Z Composer 자체에 대한 모든 변경 사항에 대한 전체 Audit 추적을 표시함으로써 이러한 내용을 확장합니다.

- 작업 생성
- Inventory 변경
- 자격 증명 저장소
- 모든 내용을 안전하게 추적

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/4role_based.png)

## 클러스터 구성
---
여러 개의 Cloud Z Composer 노드를 Cloud Z Composer 클러스터에 연결합니다. Cloud Z Composer 클러스터는 중복성과 용량을 추가하여 전사규모로 자동화를 확장할 수 있도록 지원합니다.

- 예약된 용량과 용량을 조직, Inventory 등을 기준으로 추가합니다.
- 추가 로컬 용량과 네트워크 영역 간 액세스를 위해 원격 실행 노드를 배포합니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/5cluster.png)

## 통합 Notification
---
통합 Notification를 통해 자동화 상태에 대한 정보를 지속적으로 제공하십시오. 작업이 성공하면 개인 또는 팀에 알리거나 작업이 실패할 경우 에스컬레이션합니다. 전체 조직에 대해 한 번에 통지를 보내거나 작업별로 사용자 정의하십시오. 

다음과 같은 메시지 툴에 Notification을 연결할 수 있습니다.

- SMS
- Email
- Slack
- Hipchat

> 사용자 지정 웹 후크에 Notification을 게시하여 인프라의 다른 툴을 트리거할 수 있습니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/6notification.png)

## Job 스케쥴링
---
Playbook 실행, 클라우드 인벤토리 업데이트 및 소스 제어 업데이트를 지금 실행, 나중에 실행 또는 영구적으로 실행할 수 있습니다. 

> 야간 백업, 규정 준수를 위한 주기적인 구성 업데이트 적용 또는 단 몇 번의 클릭만으로 지속적인 전체 제공 파이프라인과 같은 간헐적인 작업을 설정할 수 있습니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/7job_schedule.png)

## Inventory 관리 및 추적
---
Cloud Z Composer를 통해 다음의 클라우드 인프라를 관리할 수 있습니다.

- IBM Cloud (Softlayer)
- Amazon Web Services
- Microsoft Azure
- Google Cloud Platform
- OpenStack
- VMware

> 클라우드 인벤토리의 동기화를 유지할 수 있으며, Cloud Z Composer의 강력한 프로비저닝 콜백을 통해 노드가 온디맨드 방식으로 구성을 요청할 수 있어 자동 확장이 가능합니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/8inventory.png)

## 단순화된 셀프 서비스 제공
---
Cloud Z Composer를 사용하면 클릭 한 번으로 Playbook을 시작할 수 있습니다. 또한 변수를 묻는 메시지를 표시하고 사용 가능한 보안 자격 증명 중에서 선택하고 결과 배포를 모니터링할 수 있습니다.

> Survey : 간편한 Form builder Form을 신속히 작성하여 Cloud Z Composer 사용자로부터 작업 변수 요청할 수 있습니다.

Cloud Z Composer의 간소화된 포털 모드 및 설문 조사 기능을 통해 IT 관리자는 다음과 같은 회사 디렉토리에서 직접 동기화된 자동화 작업 실행을 조직 전체의 사용자에게 위임할 수 있습니다.

- LDAP
- Active Directory
- 위임된 SAML 인증 

> 개발자나 QA 부서는 Cloud Z Composer 위임을 통해 자체 개발 및 테스트 환경을 프로비저닝할 수 있습니다. 

>고객 서비스 에이전트는 새 데모 환경을 프로비저닝할 수 있습니다. 

>하위 관리자가 버튼 하나만 누르면 암호 변경과 같은 간단한 작업을 실행할 수 있습니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/9Survey.png)

## Remote Command 실행
---
Cloud Z Composer의 Remote Command 실행을 통해 인벤토리의 모든 호스트 또는 호스트 그룹에서 간단한 작업을 실행할 수 있습니다. 

- 사용자 또는 그룹을 추가
- 암호를 재설정
- 오작동 서비스를 다시 시작
- 중요한 보안 문제를 신속하게 패치

> Remote Command 실행은 Cloud Z Composer의 역할 기반 액세스 제어 엔진을 사용하며 모든 작업을 기록합니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/10runcommand.png)

## REST API 및 CLI 툴 제공
---
사용자 인터페이스에 국한되지 않고, Cloud Z Composer의 모든 기능을 Cloud Z Composer의 REST API를 통해 이용할 수 있으며, 이를 통해 구축할 수 있는 시스템 관리 인프라에 이상적인 API를 제공합니다. 빌드 도구에서 사용할 수 없는 작업을 호출하고 사용자 지정 대시보드에 사용할 수 없는 정보를 표시합니다.

> REST 코드를 작성하는 것보다 명령행 인터페이스를 래핑하는 것이 더 쉬운 경우, Jenkins와 같은 CI 시스템에서 작업을 시작하거나 다른 명령줄 도구와 통합해야 할 때 사용할 수 있는 Cloud Z Composer의 CLI 도구를 사용할 수 있습니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/11restapi.png)

## Source Control 정보 수집 및 동기화
---
Git, SVN 또는 Mercurial에서 Playbook 및 Inventory 수집 및 동기화

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/12source_control.png)

## Run time Job 제어
---
Job 시작 시 Credential 증명, 인벤토리, 제한, 태그 등을 제공합니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/13runtime.png)

## Credential 관리
---
- Credential security : Secret을 노출하지 않고 안전하게 암호화 및 위임
- Custom credentials : Inventory 및 Playbook에 사용할 사용자 지정 Credential 증명 유형 정의

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/14credential.png)

## Network Account 통합
---
GitHub 및 Google Apps에서 사용자 및 팀 정보 동기화 및 통합

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/15network_account.png)

## Multi tenancy
---
전체 권한 분리가 가능한 여러 조직 사용

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/16multi_tenancy.png)

## Logging 및 분석 통합
---
Logstash, Splunk등 선택한 엔드포인트로 시스템 추적 및 Cloud Z Composer 작업 실행 출력 자동 내보내기

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-docs/17logging.png)
