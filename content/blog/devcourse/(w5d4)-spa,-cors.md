---
title: (W5D4) SPA, CORS
date: 2021-09-02 17:09:37
category: devcourse
draft: false
---

## SPA - 단일 페이지 웹 애플리케이션

사용자 인터랙션에 의해 URL 변경 시 화면 전체의 로드없이 화면의 일부분만 동적으로 렌더링하여 데스크탑 애플리케이션과 비슷한 유저 경험을 제공한다.

특정 영역만 렌더링 된다. DOM 조작을 통하여 렌더링이 이루어지게 된다.

AJAX을 이용해서 JSON과 같은 데이터만 애플리케이션 실행 중에 읽어오고 관련된 화면을 변경시킨다.

HTTP Response에 대한 header, 상태 코드를 처리하기 위해 스프링에서 ResponseEntity를 제공한다. 



## CORS

하나의 웹 애플리케이션은 꼭 하나의 호스트에서 데이터를 가져와야한다는 룰이 정해져있지 않다.

사용자를 악의적인 행위로부터 보호하기 위해서 브라우저는 동일 출처에서만 리소스에 접근을 허용하게 한다. 웹 애플리케이션은 동일한 출처의 리소스에만 접근이 가능하다.

동일한 출처가 아닐 때 CORS가 발생한다.

preflight(예비 요청)을 보내고 안보내고의 차이에 따라 CORS 흐름이 바뀐다.

단순 요청이 아닐 때 예비 요청을 보낸다

CORS를 서버에서 어떻게 지원하지?
-> ResponseEntity에 헤더를 추가해서 리턴할 필요 없이 어노테이션 기반으로 설정해주거나 전역 설정을 통해 처리할 수 있다.

Jackson 이용하려면 도메인 엔티티에 디폴트 생성자 필요하다. -> 도메인은 건드리면 안되고 dto를 만들어서 해결한다. dto는 불변으로!

특정 컨트롤러에만 CORS origin을 설정하고 싶으면 해당 메서드에 `@CrossOrigin(origins = "*")` 어노테이션을 추가한다.

