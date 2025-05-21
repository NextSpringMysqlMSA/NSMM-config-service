## 🌿 Spring Cloud Config 서버 동작 흐름
```mermaid
flowchart TD
    %% 노드 정의
    start((Start))
    configInit[Spring Boot 시작]
    enableConfig[Config 서버 활성화]
    loadProps[application.yml 로드]
    connectGit[Git 저장소 연결]
    listenPort[8888 포트 대기]
    configReq[설정 요청: GET /app/profile]
    fetchConfig[Git 저장소에서 설정 조회]
    returnJson[설정 JSON 반환]
    endNode((End))

    %% 흐름 정의
    start --> configInit
    configInit --> enableConfig
    enableConfig --> loadProps
    loadProps --> connectGit
    connectGit --> listenPort
    listenPort --> configReq
    configReq --> fetchConfig
    fetchConfig --> returnJson
    returnJson --> endNode

    %% 색상 스타일 정의
    classDef forest fill:#e6f4ea,stroke:#2e7d32,stroke-width:1.5px,color:#2e7d32;
    classDef terminal fill:#d0f0c0,stroke:#1b5e20,color:#1b5e20;

    %% 클래스 적용
    class start,endNode terminal;
    class configInit,enableConfig,loadProps,connectGit,listenPort,configReq,fetchConfig,returnJson forest;
