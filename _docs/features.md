+++
title = "home"
date = 2018-10-02T15:20:00Z
weight = 1
alwaysopen = true
+++

# Cloud Z Composer를 활용한 Nginx Web Server Provisioning 예제
--- 
Cloud Z Composer는 IT 자동화의 확장, 복잡한 배치 관리 및 생산성 향상을 지원합니다. 앱 배포에서 다중 계층 조정에 이르기까지 제어, 보안 및 위임 기능을 추가하여 엔터프라이즈 자동화를 지원합니다. 시각적 대시 보드, 역할 기반 액세스 제어, 작업 스케줄링, 통합 알림 및 그래픽 인벤토리 관리로 IT 인프라를 중앙 집중화하고 제어하십시오.

> 아래의 순서대로 예제를 진행하면 Cloud Z Composer를 사용하여 보다 쉽게 Nginx Web Server를 Provisioning 할 수 있습니다.

## 1. Cloud Z Composer의 docker-compose 소스 및 Provisioning 예제소스 위치
---

Cloud Z Composer의 docker-compose 소스 및 Provisioning 예제소스 위치 URL은 다음과 같습니다.

- https://github.com/skcloud/zcomposer-demo


![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/1_github_main.png)

## 2. Z Composer의 docker-compose 소스 및 Provisioning 예제소스 사용을 위한 Git Repository Fork 방법 
---
Z Composer의 docker-compose 소스 및 Provisioning 예제소스를 사용하기 위해서는 본인 계정의 Git Repository로 Fork 해야 합니다. 방법은 다음과 같습니다.

1. 예제 소스 Git에서 우측 상단에 있는 Fork 버튼 클릭
2. 본인 계정의 Git으로 아래 1번째 이미지와 같이 Fork가 되는 것을 확인
3. Fork가 완료되면 아래 2번째 이미지와 같이 본인 계정 내 예제 소스의 Repository가 생성된것을 확인 할 수 있다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/2_fork_repo.png)
![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/3_forked_github.png)

## 3. Cloud Z Composer의 docker-compose 소스 및 Provisioning 예제소스 Repository Clone
---
Cloud Z Composer의 docker-compose 소스 및 Provisioning 예제소스를 다음과 같은 명령어로 Repository를 Clone 합니다.

- git clone <앞에서 Fork된 예제소스의 Repository URL>

> Clone 된 zcomposer-demo 디렉토리 현황 및 docker-compose 소스는 다음과 같습니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/4_git_clone_and_docker.png)


## 4. Cloud Z Composer 기동
---
Cloud Z Composer는 다음과 같은 명령어를 이용하여 기동합니다.

- docker-compose up -d

> 해당 명령어는 docker-compose 파일이 있는 디렉토리 내에서 실행합니다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/5_docker-compose2.png)

기동 여부를 다음과 같은 명령어로 확인합니다.

- docker ps

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/6_docker_ps.png)

## 5. Cloud Z Composer 접속
---
Cloud Z Composer는 Local에 띄운 경우 다음과 같은 정보로 접속하면 된다.

- URL : http://localhost:80
- ID : admin
- Password : password

> Password는 로그인 후 Users 메뉴에서 변경 할 수 있다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/7_z_composer_login.png)

로그인을 성공하면 제일 먼저 확인할 수 있는 화면은 바로 Dashboard 이다.
각 메뉴에 대한 용도는 다음과 같다.

Views
- Dashboard : Cloud Z Composer 전체 현황 출력 (Host, Inventory, Project, Job등)
- Jobs : Cloud Z Composer Job(작업) 실행 이력. 최근부터 과거까지 내림차순으로 출력
- Schedules : Schedule 적용된 Job 목록
- My View : 실행가능한 Job Template 목록 및 Job 실행 이력

Resources
- Templates : Job Template 관리
- Credentials : 원격호스트 접속용 Credential 관리 (Host, Github등)
- Projects : Job으로 사용될 Playbook, Role 관리
- Inventories : Cloud Z Composer를 사용할 수 있는 Host 및 Host의 Group 관리
- Inventory Scripts : Inventory를 자동으로 관리할 수 있는 Script 목록 관리

Access
- Organizations : User의 대그룹. 보통 회사 및 단체 단위로 지정한다.
- Users : User 관리. 메뉴 접근 및 사용 권한을 제어할 수 있다.
- Teams : User의 그룹 보통 팀이나 부서 단위로 제어 할 수 있다. 

> 각 메뉴에 대한 상세 설명은 Usecase를 통해 같이 설명될 예정이다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/8_main.png)

## 6. Inventory Script를 이용한 자동 Inventory 관리
---
Cloud Z Composer에서는 Inventory Script를 통해 자동으로 Inventory에 대한 다음의 기능을 관리할 수 있다.

- Inventory 내 Host 자동 등록 (Host의 경우 VM 외에 Baremetal, Storage(Volume), Network등 Cloud API로 통신 가능한 대상 모두 적용가능하다)
- Host별 자동 Grouping (Group은 Cloud API로 제공 가능한 공통적인 정보들을 활용하여 적용할 수 있다)
- Host 생성, 변경, 삭제 Job 수행시 Inventory 내 갱신

---

Cloud Z Composer Demo 소스를 활용하여 Inventory 내 자동 Host 및 Group 등록을 사용할 수 있다.

본인의 Github Repository에 있는 다음의 경로에서 다음의 항목을 수정한다. (경로 : zcomposer-demo/inventory_script/softlayer/vm-host.py)
- softlayer_username : 본인의 IBM Softlayer 계정명을 입력한다. (예 : 1234567_본인 이메일명@도메인명)
- softlayer_api_key : 본인의 IBM Softlayer API Key를 입력한다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/9_set_inventory_script.png)

수정된 Inventory Script 코드를 다음과 같은 절차 진행후 복사한다.

1. Dashboard에서 Inventory Script 메뉴 클릭
2. 우측 상단에 + 버튼(Create a new custom inventory) 클릭
3. Name 입력. Name은 관리할 Cloud Platform명 - 종류명과 일치하도록 한다. (예 : Softlayer-VM)
4. Organiztion의 경우 있으면 선택. 없을 경우 Default로 사용
5. 본인 Github Repository에서 수정된 Inventory Script 코드를 복사하여 Custom Script 부분에 붙여넣기 한다.
6. Save 버튼을 눌러 저장

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/10_apply_inventory_script.png)

> Inventory Script 메뉴를 다시 누르면 위에서 등록한 Inventory Script 항목이 추가된 것을 확인 할 수 있다.

## 7. Inventory 생성 및 Host 등록
---
Cloud Z Composer의 Inventory 기능을 통해 다음과 같은 요소를 관리 할 수 있습니다.

- Host 추가/수정/삭제 (Local, Remote)
- Group 추가/수정/삭제
- 다양한 종류의 장비 지원 (VM/서버/스토리지/네트워크/보안장비)
- Inventory Script와 연동하여 자동화 관리

> Inventory명은 관리할 Cloud Platform명 - 종류명과 일치하도록 한다. (예 : Softlayer-VM)

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/11_apply_inventory.png)

---
Inventory 탭중에 Sources라는 탭을 누르면 앞서 생성한 Inventory Script를 연동하여 Host 및 Group을 자동으로 등록, 관리 할 수 있도록 기능을 제공한다.

등록시 다음 항목을 필수로 등록한다.

- Name : Inventory Source명. 명시적으로 구분지을수 있도록 이름을 생성한다.
- Source : Custom Script를 선택. Custom Script은 앞서 생성한 Inventory Script를 뜻하여 선택을 해야 조회가 가능하다.
- Custom Inventory Script : 앞서 생성한 Inventory Script중에서 현재 Inventory용으로 사용될 Inventory Script 선택
- Verbosity : 출력 로그 수준. 보통은 1 (Info) 수준으로 하며, 자세한 Debug가 필요한 경우에는 2 (Debug)를 선택한다.


> 위에 명시된 부분을 모두 입력(선택) 한 뒤에 Save 버튼을 클릭하면 저장되며, Inventory Source가 등록되어 리스트에 출력 된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/12_create_inventory_sync.png)

---
Inventory Sync는 Inventory Source가 등록되면 다음과 같은 순서대로 수행 할 수 있다.

1. Inventory Sources 항목중 Sync 대상 확인
2. Actions 열에 두번째 아이콘(Sync) 클릭
3. Sync가 진행되면 좌측 Sources 부분에 초록색 구름이 커졌다 작아졌다를 반복하며 Sync를 진행함 (구름을 클릭하여 Sync Job 상세진행내역도 확인가능)
4. 정상적으로 완료되면 초록색 구름 상태로 크기가 유지됨 (실패할 경우 빨간색 구름 표시, 클릭하면 실패 내역 확인 가능)
5. Inventory의 Hosts 탭을 클릭하여 Sync된 Host목록을 확인 할 수 있다.

> Inventory Sources List의 모든 항목에 대한 Sync를 동시에 수행하고자 할 경우, 우측에 있는 Sync All 버튼을 클릭하면 동시에 Sync가 진행된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/13_inventory_sync.png)


Sync가 완료되고, Host 탭을 클릭하면 본인 계정의 클라우드에 있는 호스트의 정보가 목록화 되어 출력된다.

- Hosts 열에는 호스트명이 출력된다.
- Related Groups 열에는 기본적으로 설정된 Grouping Tag가 출력된다.

> Grouping Tag는 OS버전, 기본 스펙(CPU,Memory), Zone명, 도메인명이 출력된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/14_sync_inventory.png)

Hosts열의 특정 호스트명을 클릭하면 해당 호스트의 상세정보를 확인할 수 있다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/15_host_detail.png)

## 8. Credential 관리
---
원격호스트 접속용 Credential 관리 (Host, Github등)를 이곳에서 할 수 있다.

Credential 생성 방법은 다음과 같다.

1. 우측에 있는 + 버튼 클릭
2. Name 입력 (Name은 어떤곳에서 사용하는 Credential인지 명시적으로 나타내야 한다.)
3. Credential Type 선택 (Credential Type은 다음의 항목중 특정 항목을 선택할 수 있다.)
* Machine : 특정 호스트 접속시 사용되는 Credential. ID/PW 및 SSH Key등을 사용할 수 있다.
* Source Control : 특정 SCM 접속시 사용되는 Credential. SCM은 대표적으로 Git을 사용할 수 있다. ID/PW 및 SSH Key등을 사용할 수 있다.
* Cloud Provider : 특정 Cloud Provider 접속시 사용되는 Credential. Cloud Provider는 AWS, Azure, GCP, Openstack, VMware등이 있다.
4. Username : 사용자의 접속 ID
5. 비밀번호 : 사용자의 접속 비밀번호(Password)
6. Private Key : 사용자의 접속용 Key (SSH 등)
7. Privilege escalation 항목 (Machine Type 선택시)
* Privilege Escalation Method : 권한 관련 처리기능 선택 (sudo, su)
* Privilege Escalation Username : 권한 관련 기능 사용자명
* Privilege Escalation Password : 권한 관련 기능 사용자의 비밀번호
8. Save 버튼을 클릭하여 Credential 저장

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/16_create_credential.png)

저장된 Credential은 다음과 같이 목록에 추가되어 추후 Project 생성시 특정 SCM 접근용 및 Template 생성시 특정 호스트 접근용으로 사용되어진다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/17_credential_list.png)

---

VM(서버) 접속용 SSH Key를 Credential로 등록하는 방법은 다음과 같다. 

1. Name : 접속할 VM(서버)를 명시적으로 나타내는 제목 입력
2. Credential Type : VM(서버)를 접속하기 위해서는 Machine으로 선택한다.
3. SSH Private Key : 이곳으로 SSH Private Key를 복사후 붙여넣기 한다. 붙여지면 SSH Key는 출력되지 않는다.(Encrypted로 표시)
4. Save 버튼을 클릭하면 VM(서버) 접속용 SSH Key Credential이 생성된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/21_create_vm_ssh_key.png)

목록에 추가된 SSH Credential을 확인 할 수 있다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/22_add_credential_list.png)

## 9. Project 관리
---
Job으로 사용될 Playbook, Role 관리를 이곳에서 수행한다.

앞서 Forked된 zcomposer-demo Repository에서 다음의 경로로 이동하여 생성할 VM에 대한 정보를 요구사항에 맞추어 수정한다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/17-5_set_vm_info.png)


Project 관리를 위해 다음과 같은 순서로 진행한다.

1. Project 관리페이지에서 우측의 + 버튼 클릭
2. Name은 Project명을 구분할 수 있도록 명시적으로 지정한다.
3. Organization은 있을 경우 선택하여 지정한다. 만일 없을 경우 보통 Default로 지정한다.
4. SCM Type은 여러가지가 있으나, 보통은 Git으로 지정한다. Git으로 지정하면 Github 및 Gitlab 모두 같은 기능으로 연동해 사용가능하다.
5. SCM Credential은 SCM이 Private 형태로 사용될 때 접근을 위한 Credential을 선택할 수 있다. Credential은 8번에서 설명한 방법대로 생성하면 이곳에서 선택이 가능하다. (Credential Type : Source Control)
6. Save를 클릭하면 Project가 생성되고 목록에 추가된다.
7. 목록에 추가되자마자 자동으로 Project Sync가 실행된다. 통신에 문제가 없으면 현재 기준으로 Sync가 완료되어 원격지에 있는 Playbook 혹은 Role을 Z Composer에서 사용가능해진다.

> Project Sync가 실패한경우 원격지와의 통신 혹은 Credential 문제를 확인해야 한다. Credential 문제에 경우는 8번과 같이 원격지 정보를 등록하며 Project의 SCM Credential로 선택하면 로그인 및 접근이 가능해진다. 

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/18_create_project.png)

Project 등록이 완료되면 목록에 추가된것을 확인할 수 있다.

> 현재 기준으로 Project를 Sync하고자 할 때에는 해당 항목 우측의 Actions 열에 있는 원 화살표 모양(Get latest SCM revision)을 클릭하면 Sync가 된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/19_project_list.png)

## 10. Template 관리
---
Job Template 관리를 이곳에서 수행한다.

Job Template 생성은 다음과 같은 순으로 생성해 Job을 수행할 예정이다. (Cloud Z - Softlayer 기준)

1. Create compute VM (Compute용 VM 생성)
2. OS Provisioning (OS 세팅)
3. Install Nginx (Nginx Web 서버 설치, 기동)

Template 메뉴에서 + 버튼을 클릭해 Job Template를 다음과 같은 부분을 설정한다.

---

1.Create compute VM (Compute용 VM 생성)은 다음의 항목을 기입한다.

* Name : Job을 명시적으로 표현할 제목 (보통은 [Cloud Provider명] 순번, Job 수행명을 명시)
* Job Type : Job 수행방식. Run은 실제 Job 수행, Check는 Dry run으로 예상되는 Job의 실행방식을 표시한다.
* Inventory : Inventory 선택. 7번과 같은 방식으로 생성된 특정 Inventory를 선택한다.
* Project : Project 선택. 9번과 같은 방식으로 생성된 특정 Project를 선택한다.
* Playbook : Project내 포함된 특정 Playbook 선택. Playbook은 실제 Job이 되는 작성된 코드이다.
* Verbosity : Job 수행시 출력되는 로그 수준. (1 ~ 2 Info Verbose, 3 ~ 4 Linux Debug, 5 Windows Debug가 가능하다.)

> 작성후 Save 버튼을 클릭하면 Template 목록에 Job Template이 추가된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/20_create_vm_template.png)

2.OS Provisioning (OS 세팅)은 추가적으로 다음의 항목을 기입한다. (기본 항목은 상기 1번 참조)

* Credential : Job 수행 대상이 되는 VM(서버)에 접속하기 위해 기 생성된 SSH Credential을 선택
* Limit : Inventory에 등록된 Host중 특정 호스트명 대상으로만 Job을 수행하고자 할 때나 특정 Group으로 묶여진 Host대상으로 Job을 수행하고자 할 때 이 부분을 사용한다. Regex와 같이 다음과 같은 정규 표현식을 사용할 수 있다.
    * \* (별표) : 별표가 들어간 부분은 임의의 어떠한 문자열도 포함할 수 있다. (예 : 192.0.2.*)
    * : (콜론) : 앞뒤 문자열의 OR 조건의 문자열에 해당되면 포함할 수 있다. (예 : webservers:dbservers)
    * :& (콜론앤드) : 앞뒤 문자열의 AND 조건의 해당되는 문자열만 반드시 포함할 수 있다. (예 : webservers:&staging)
    * :! (콜론느낌표) : 뒤 문자열을 제외한 조건의 문자열만 반드시 포함할 수 있다. (예 : webservers:!phoenix)

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/23_os_provisioning_template.png)

3.Install Nginx (Nginx Web 서버 설치, 기동)은 추가적으로 다음의 항목을 기입한다. (기본 항목은 상기 1, 2번 참조)

* Extra Variables : Project의 Playbook내에서 사용되는 Variable(변수)의 Value값을 Job 실행전 임의의 값으로 변경하여 사용할 수 있다. 
> 아래의 캡쳐와 같이 Extra Variables에 명시된 "ansible_port: 2202" 부분은 기본(Default) Port인 22에서 2202로 변경해 Job을 실행하겠다고 변수를 명시한 것이다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/24_install_nginx_template.png)

Template은 Job Template외 Workflow Template도 입력이 가능하다. 
> Workflow는 여러개의 Job을 순차적으로 구성해 표시한 Grouping된 Job이다. 

Template 메뉴에서 + 버튼을 클릭해 Workflow Template를 다음과 같은 부분을 설정한다.

1. Name : Workflow를 대표할 제목을 명시한다.
2. 상단의 Workflow Visualizer를 클릭하여 Workflow로 구성될 Job Template을 순차적으로 구성할 수 있다. (상세 구성방법은 하기 참조)
3. Workflow Visualizer까지 구성 완료되고 Save 버튼을 클릭하면 Template 목록에 추가 된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/25_create_workflow_template.png)

Workflow Visualizer는 다음과 같은 기능을 이용하여 Job Template을 순차적으로 구성할 수 있다.

1. Start라고 표시된 초록색 사각형을 클릭하면 가상의 사각형이 연결되면서 우측의 항목을 선택해 추가할수 있도록 제공된다.
2. 우측의 항목은 다음과 같다.

    * Jobs : Job Template의 목록을 표시. Job Template을 선택하면 해당 순서에서 Job을 실행할 수 있다.
    * Project Sync : Project의 목록 표시. Project를 선택하면 해당 순서에서 Project를 현재 기준으로 Sync하게 된다. (사각형에 P 표시가 붙음)
    * Inventory Sync : Inventory Source의 목록 표시. Inventory Sync를 선택하면 해당 순서에서 Inventory를 현재 기준으로 Sync하게 된다. (사각형에 I 표시가 붙음)
3. 우측의 항목중 특정 항목, 요소를 선택한 뒤에 Select 버튼을 클릭하면 해당 순서의 사각형이 활성화 하게 된다.
4. 활성화 된 사각형에서 다음 순서의 Job을 이어가려면 마우스 오버를 하면 추가 아이콘이 사각형 오른쪽에 나타난다.

    * \+ 버튼 : 다음 순서의 Job이 되는 가상의 사각형을 만들고 연결. Job 선택 항목 활성화
    * \- 버튼 : 해당 순서의 Job 삭제. 삭제시 경고창이 뜬다. 삭제가 되면 해당 순서는 없어지며, 다음 순서의 Job이 있을 경우 현재 순서로 앞당겨진다.
5. \+ 버튼을 누르면 Job 선택 항목 활성화 되며, 중간에 있는 Run 기능에서 Job 실행 조건을 선택할 수 있다.

    * On Success : 전단계 Job이 무조건 성공시 이번 Job이 실행
    * On Failure : 전단계 Job이 무조건 실패시 이번 Job이 실행
6. 동시에 분기 실행이 가능하다. 현재 Job에서 다음 Job을 생성, 연결한뒤에 현재 Job을 재 클릭하여 다음 Job과 다른 Job을 선택하면 분기된 다음 Job이 추가로 생성, 연결된다. (개수 제한 없음)
7. Workflow Visualizer 구성이 완료되면 우측 하단의 Save 버튼을 클릭하여 저장한다.
8. Workflow Template 설정이 완료되면 우측의 Save 버튼을 클릭하여 저장한다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/26_design_workflow.png)

새로 생성된 Job Template 및 Workflow Template은 Template 메뉴에서 목록을 확인 할 수 있다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/27_template_list.png)

## 11. Job 실행
---
Job 실행은 보통 My View 메뉴에서 수행한다. (Dashboard, Jobs, Templates에서도 수행 가능)

> My View는 실행가능한 Job Template 목록 및 Job 실행 이력을 보여준다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/28_job_list.png)

Job 실행은 각 Job 항목의 우측에 있는 로켓(Start a job using this template) 버튼을 클릭하여 수행한다.

* 예제에서는 앞서 생성한 Workflow Template의 로켓버튼을 클릭한다.
* Job을 실행하면 다음과 같은 화면이 출력되며, Status는 Running중으로 된다. (진행되는 부분은 원이 커졌다 작아졌다로 표시)
* Workflow 내의 Job은 좌에서 우로 순차적으로 진행된다. (진행되는 부분은 원이 커졌다 작아졌다로 표시)
* 진행되는 Job의 상세 진행로그를 확인하고자 하면 Detail 링크를 클릭하면 된다. (자세한 내용은 아래 첨부된 캡쳐 참조)
* Workflow Job 실행을 취소하고자 할 때에는 로켓 옆에 있는 금지 표시를 누르면 Job이 중단된다. (Rollback 기능은 없기 때문에 이미 진행된 Job내 Task는 되돌릴수 없다.)
* 확장표시를 누르면 Workflow UI만 화면에 출력된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/29_createing_vm.png)

VM 생성 Job이 실행중인 경우 본인의 Cloud 계정에서 확인해보면 실제 VM이 다음과 같이 생성되는걸 확인할 수 있다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/30_createing_vm_in_softlayer.png)

특정 Job의 Detail 링크를 클릭하면 다음과 같이 상세 진행로그를 확인할 수 있다.

* Status는 Running중으로 된다. (진행되는 부분은 원이 커졌다 작아졌다로 표시)
* Finished 부분은 Not Finished로 표시된다.
* 진행되는 Job의 상세 진행로그는 Job 내부에 진행되는 Task별로 순차적으로 출력되며 성공/실패 결과값은 마지막에 출력된다. (각 로그는 실행 기준으로 수행 시작 시간을 표시한다.)
* Job에 대한 다음의 정보가 우측 상단에 표시된다.
    * Plays : 현재 Job으로 실행되는 Playbook의 수
    * Tasks : Job에 포함된 Task 수
    * Hosts : Job이 수행되는 대상 호스트의 수
    * ELAPSED : 경과 시간으로, 실시간으로 표시된다.
    * 확장표시를 누르면 로그만 화면에 출력된다.
* Job 실행을 취소하고자 할 때에는 로켓 옆에 있는 금지 표시를 누르면 Job이 중단된다. (Rollback 기능은 없기 때문에 이미 진행된 Job내 Task는 되돌릴수 없다. 취소가 되면 해당 Job은 Cancelled로 표시)

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/31_creating_vm_logs.png)

VM 생성시 VM 접속용 SSH Key Pair도 등록하게 된다. (등록해야 접속가능)

> 등록된 정보는 본인 계정의 SSH Key Pair 부분을 확인하면 된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/32_created_ssh_key.png)

Job이 실행이 완료되면 다음과 같은 결과가 출력된다.

* Status는 Successful로 출력 된다. (실패하면 Failed로 표시)
* Finished 부분은 완료된 시간이 표시된다.
* 우측 상단의 Elapsed의 경우 Job 시작 ~ 종료 시간의 총 소요시간이 표시된다.
* 성공/실패 결과값은 다음과 같은 순서로 표시된다.
    * OK : Task 성공 횟수
    * Changed : 변경이 반영된 횟수
    * unreachable : 연결이 안된 횟수
    * Failed : Task 실패 횟수

---
1.Create compute VM (Compute용 VM 생성)후 최종 실행한 결과 이다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/33_successful_job.png)

Cloud Z - Softlayer Inventory Source를 Sync 한 뒤 최종 실행한 결과 이다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/34_successful_inventory_sync.png)

2.OS Provisioning (OS 세팅)후 최종 실행한 결과 이다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/35_successful_os_provisioning.png)

3.Install Nginx (Nginx Web 서버 설치, 기동)후 최종 실행한 결과 이다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/36_successful_install_nginx.png)

Workflow가 정상적으로 수행 완료된 결과이다. (상기 4개 Job이 순차적으로 구성)

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/37_successful_all_job.png)

## 12. Job 실행 결과 확인
---
Job 실행 결과는 다음의 부분을 확인 할 것이다.

1. Inventory에서 Host로 VM 생성정보 등록 확인
2. 원격으로 Nginx Web서버 기동 확인
3. Dashboard에서 Job 현황 확인

---
1.Inventory에서 Host로 VM 생성정보 등록 확인

* Inventories 메뉴에서 특정 Cloud Provider (여기서는 Softlayer)를 클릭하면 Host 현황이 표시된다. (Host 탭 클릭)
* Host 현황중 이번에 생성된 VM만 확인하고자 할 때에는 검색키로 호스트명 일부만 입력해도 검색해준다.
* 검색키를 포함한 호스트가 출력되면 호스트명 및 관련된 그룹명이 출력된다.
* 상세정보를 확인하고자 하면 호스트명 링크를 클릭하면 된다.

> 여기서는 이번 Job 실행을 통해 생성된 VM 1개의 정보가 출력된다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/38_created_vm_apply_inventory.png)

2.원격으로 Nginx Web서버 기동 확인

* Host의 상세항목중 Key명이 ansible_host로 등록된 부분의 Value가 바로 해당 VM의 Public IP이다.
* Public IP를 브라우져에 입력하면 Nginx Web 서버에 접속할 수 있음을 확인할 수 있다. (하기 참조)

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/40_running_nginx.png)

3.Dashboard에서 Job 현황 확인

* 추가된 VM 만큼 Hosts의 숫자가 증가된다.
* 추가된 Inventory 만큼 Inventories의 숫자가 증가된다.
* 추가된 Project 만큼 Projects의 숫자가 증가된다.
* Job Status를 통해 일일 성공/실패 내역이 그래프로 표시된다.
* 상기 생성된 최근 Job Template 및 최근 실행된 Job의 현황은 Dashboard에서 확인 가능하다.

![cloudZ](https://seo01.objectstorage.softlayer.net/v1/AUTH_a24ffe9e-6cac-4383-a870-99a6582e7964/zcomposer-demo/41_recently_job.png)

---
