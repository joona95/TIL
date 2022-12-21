# Github Action

- 빌드, 테스트 및 배포 파이프라인 자동화할 수 있는 CI/CD 플랫폼

- 각 workflow는 해당 github repository의 .github/workflows에 YAML 파일로 저장됨

- 직접 작성 가능하지만 템플릿 활용 가능

## 컴포넌트

### workflows

- 가장 최상위 개념으로 하나 이상의 job으로 구성됨

- 다양한 job으로 구성되며 기본적으로 병렬적으로 jobs 실행

- event에 의해 트리거될 수 있는 자동화된 프로세스

- Gihub Repository의 .github/workflows 폴더 아래에 YAML 으로 작성됨

- 하나의 repository는 여러 workflow 가질 수 있으며 각 workflow는 서로 다른 작업 수행 가능

- 민감 정보 사용 시 Github > Settings > secrets 에 저장하여 환경 변수로 사용 가능 

    ```
    ${{ secrets.KEY }}
    ```

### events

- workflow 실행을 트리거하는 특정 활동이나 규칙

### jobs

- 여러 step으로 구성되고 가상 환경의 인스턴스에서 실행됨

- 다른 job에 의존 관계 가질 수 있으며, 독립적으로 병렬 실행도 가능

- needs: 의존 관계 설정해 순서 정의 가능

### steps

- 특정 action을 실행할 수 있음

- uses: 사용할 action 지정

- name: 해당 step의 이름 

- run: runner에서 command를 실행하도록 지시. 환경변수 설정도 가능.

### actions

- workflow의 가장 작은 블럭

- job을 만들기 위해 step들을 연결할 수 있음

### runners

- workflow가 트리거될 때 실행하는 서버

- 각 runner는 1번에 1개의 job을 실행할 수 있음

## runs-on

- 어떤 OS에서 실행될지 지정

- ubuntu-latest는 ubuntu 최신 버전에서 실행됨을 의미함

