# Spring Boot + RabbitMQ
* RabbitMQ는 AMQP 프로토콜을 구현한 메시지 큐

### AMQP
* AMQP는 exchange, queue, binding 세가지 중요 컴포넌트로 구성된다.
    * exchange : 발행자로부터 수신한 메시지를 큐 또는 다른 exchange로 보내는 라우터 역할.<br/>
    이때 exchange는 exchange type과 binding이라는 몇 가지 규칙을 따르는 라우팅 알고리즘에 의해 움직인다.
        * exchange type은 <code>기본, 직접, 팬아웃, 토픽, 헤더</code> 5가지가 있습니다.
            1. 기본(default): 생성한 큐에 모두 자동 바인딩
            2. 직접(direct): 라우팅 키와 큐를 1대1 바인딩
            3. 토픽(topic): 라우팅 키에 와일드카드를 추가해서 바인딩할 수 있다.
            4. 헤더(headers): 메시지 헤더에 따라 바인딩하는 기능(헤더에 표현식을 쓰면 무엇이든 가능한 아주 강력한 exchange)
            5. 팬아웃(fanout): 메시지를 바인딩한 큐 전체에 복사한다. 즉, 메시지를 방송하는 셈
        * <code>핵심</code>은 라우팅 키와 함께 메시지를 exchange로 보내면 exchage type별로 메시지를 큐로 보낸다는 것
        * <code>(라우팅 키가 맞지 않으면 전달하지 않는다.)</code>