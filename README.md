# 키친포스

## 퀵 스타트

```sh
cd docker
docker compose -p kitchenpos up -d
```

## 요구 사항
- 키친포스를 구현한다
- 키친포스는 카테고리 (MenuGroup), 메뉴 (Menu), 주문 (Order), 테이블 (OrderTable), 상품(Product)로 이루어져 있다.
- 카테고리 (MenuGroup)
  - [ ] 카테고리는 아이디와 이름으로 구성되어 있다.
  - [ ] 카테고리 아이디는 임의의 아이디로 되어있다.
  - [ ] 카테고리를 조회할 수 있다.
  - [ ] 카테고리를 생성할 수 있다.
      - [ ] 이름이 비어있으면 생성할 수 없다.
- 메뉴 (Menu)
  - [ ] 메뉴는 아이디, 이름, 가격, 노출 유무, 메뉴 그룹 아이디로 구성되어 있다.
  - [ ] 메뉴의 아이디는 임의의 아이디로 되어있다.
  - [ ] 메뉴 목록을 조회할 수 있다.
  - [ ] 메뉴를 추가할 수 있다.
      - [ ] 가격이 없거나, 가격이 0원 이하이면 메뉴를 추가할 수 없다.
      - [ ] 추가할 메뉴에 대해 카테고리가 존재하지 않으면 추가할 수 없다.
      - [ ] 메뉴 상품 목록이 비어있으면 메뉴를 추가할 수 없다.
      - [ ] 메뉴 상품 목록을 통하여 상품 목록을 조회할 수 있다.
          - [ ] 조회 한 상품 목록이 메뉴 상품 목록에 대해 갯수가 일치하지 않으면 메뉴를 추가할 수 없다.
      - [ ] 메뉴 상품 목록에 있는 각 상품에 대해 수량을 체크하여, 수량이 0인 상품이 있다면 메뉴를 추가할 수 없다.
      - [ ] 메뉴 상품 목록에 있는 각 상품 아이디를 통하여 상품을 찾을 수 있다.
          - [ ] 상품이 없다면 메뉴를 추가할 수 없다.
      - [ ] 메뉴 상품은 각 상품에 대한 가격과 수량을 곱한 것에 대해 모두 더하여 가격이 책정된다.
          - [ ] 측정 된 가격이 0원 이하면 메뉴를 추가할 수 없다.
      - [ ] 이름이 없거나, 이름에 비속어가 들어가 있으면 메뉴를 추가할 수 없다.
  - [ ] 메뉴의 가격을 변경할 수 있다.
      - [ ] 가격이 없거나, 가격이 0원 이하면 변경할 수 없다.
      - [ ] 메뉴가 존재하지 않으면 가격을 변경할 수 없다.
      - [ ] 메뉴의 가격이 메뉴의 수량에 대한 값보다 작으면 변경할 수 없다.
  - [ ] 비공개 된 메뉴를 공개할 수 있다
      - [ ] 메뉴가 존재하지 않으면 메뉴를 비공개할 수 없다.
      - [ ] 메뉴의 가격이 메뉴의 수량에 대한 값보다 작으면 공개할 수 없다.
  - [ ] 공개 된 메뉴를 비공개할 수 있다.
      - [ ] 메뉴가 존재하지 않으면 메뉴를 비공개할 수 없다
- 주문 (Order)
  - [ ] 주문은 아이디, 주문 타입, 주문 상태, 주문 시간, 주문한 상품 정보, 주소, 주문 아이디로 이루어져 있다.
  - [ ] 주문 아이디는 임의의 아이디로 되어있다.
  - [ ] 주문 타입은 배달, 테이크 아웃, 안에서 먹기가 있다.
  - [ ] 주문 상태는 대기 중, 주문 받기 완료, 주문 서빙 완료, 배달 중, 배달 완료, 주문 처리 완료가 있다.
  - [ ] 주문 목록을 조회할 수 있다.
  - [ ] 공통
    - [ ] 주문을 받을 수 있다.
      - [ ] 주문이 존재하지 않으면 주문을 받을 수 없다.
      - [ ] 주문 상태가 수락한 상태가 아니면 주문을 받을 수 없다.
    - [ ] 주문을 수락할 수 있다.
      - [ ] 주문 상태가 기다리는 중이 아니라면 주문을 수락할 수 없다.
    - [ ] 주문을 할 수 있다.
      - [ ] 주문 타입이 없다면 주문을 할 수 없다.
      - [ ] 주문한 메뉴가 없거나, 비어있다면 주문을 할 수 없다.
      - [ ] 주문한 메뉴가 메뉴 목록에 없다면 주문을 할 수 없다.
      - [ ] 주문한 메뉴가 비공개 되어있다면 주문을 할 수 없다.
      - [ ] 주문한 메뉴의 가격과 등록 된 메뉴의 가격이 다른 경우 주문을 할 수 없다.
      - [ ] 주문한 경우 초기 값은 대기 중으로 되어진다.
      - [ ] 주문 타입이 배달인 경우 빈칸이면 주문을 할 수 없다.
  - [ ] 배달을 할 수 있다.
    - [ ] 주문을 할 수 있다. 
      - [ ] 배달 주문을 한 경우 주문한 수량이 0인 경우에는 주문을 할 수 없다.  
    - [ ] 배달 주문 수락 시 배달정보(주문 번호, 가격, 주소)를 배달 기사에게 전달한다.
    - [ ] 배달 주문을 시작을 할 수 있다.
      - [ ] 주문이 존재하지 않으면 배달 주문을 시작할 수 없다.
      - [ ] 주문 타입이 배달이 아닌 경우 배달 주문을 시작할 수 없다.
      - [ ] 주문 상태가 주문 받기 완료 상태가 아니면 배달 주문을 시작할 수 없다.
    - [ ] 주문에 대해 배달을 완료할 수 있다.
      - [ ] 주문이 존재하지 않으면 배달을 완료할 수 없다.
      - [ ] 주문 상태가 배달 중이 아니라면 배달을 완료할 수 없다.
    - [ ] 주문을 완료한다.
      - [ ] 주문 타입이 배달인 경우, 주문 상태가 배달 완료가 아닌 경우에는 주문을 완료할 수 없다.
  - [ ] 테이크 아웃을 할 수 있다.
    - [ ] 주문을 완료한다. 
      - [ ] 주문 받기 완료 상태가 아니라면 주문 완료를 할 수 없다.
    - [ ] 주문을 할 수 있다. 
      - [ ] 테이크 아웃 주문을 한 경우 주문한 수량이 0인 경우에는 주문을 할 수 없다.
  - [ ] 안에서 먹을 수 있다.
    - [ ] 주문을 할 수 있다.
      - [ ] 존재하지 않는 테이블에서 주문을 할 수 없다.
      - [ ] 테이블이 비어있다면 주문을 할 수 없다.
    - [ ] 주문을 완료한다.
      - [ ] 주문 받기 완료 상태가 아니라면 주문 완료를 할 수 없다.
      - [ ] 주문 상태에 대해 주문 테이블 정보가 있고 주문 완료 상태가 완료가 아닌 경우 주문 테이블 정보 중 인원을 0명으로 만들고 비어있도록 상태를 변경한다.
- 주문 상품 정보 (OrderLineItem)
  - [ ] 주문 상품 정보는 메뉴 아이디, 수량, 가격으로 이루어져 있다.
  - [ ] 주문 상품 아이디는 임의의 아이디로 되어있다.
- 테이블 (OrderTable)
  - [ ] 테이블은 아이디, 이름, 손님 숫자, 착석 유무로 이루어져 있다.
  - [ ] 테이블의 아이디는 임의의 아이디로 되어있다.
  - [ ] 테이블 목록을 조회할 수 있다.
  - [ ] 테이블을 추가할 수 있다.
      - [ ] 이름이 없거나, 이름에 빈값이 들어가 있으면 추가할 수 없다.
  - [ ] 테이블에 착석할 수 있다.
      - [ ] 테이블이 존재하지 않으면 테이블에 착석할 수 없다.
  - [ ] 테이블을 비울 수 있다.
      - [ ] 테이블이 존재하지 않으면 테이블을 비울 수 없다.
      - [ ] 주문 테이블에 주문이 있고 주문의 상태가 완료된 상태가 아니라면 테이블을 비울 수 없다.
  - [ ] 테이블에 앉은 손님의 수를 변경할 수 있다.
      - [ ] 손님의 수가 0 이하면 손님의 수를 변경할 수 없다.
      - [ ] 테이블이 존재하지 않으면 손님의 수를 변경할 수 없다.
      - [ ] 주문 테이블이 착석되지 않은 상태면 손님의 수를 변경할 수 없다.
- 상품 (Product)
  - [ ] 상품은 아이디, 이름, 가격으로 구성되어 있다.
  - [ ] 상품의 아이디는 임의의 아이디로 되어있다.
  - [ ] 상품 목록을 조회할 수 있다.
  - [ ] 상품 아이디를 통하여 상품 가격을 변경할 수 있다.
      - [ ] 가격이 없거나, 가격이 0원 이하이면 가격을 변경할 수 없다.
      - [ ] 상품 아이디에 대한 상품이 존재하지 않으면 가격을 변경할 수 없다.
      - [ ] 상품이 메뉴에 등록되어 있다면 메뉴에 등록 된 상품의 가격과 수량을 곱한 값이 상품의 가격보다 낮은 경우 메뉴를 숨긴다.
  - [ ] 상품을 추가할 수 있다.
      - [ ] 상품을 추가하므로써 아이디, 이름, 가격을 넣을 수 있다.
      - [ ] 가격이 없거나, 가격이 0원 이하이면 상품을 추가할 수 없다.
      - [ ] 이름이 없거나, 이름에 비속어가 들어가 있으면 상품을 추가할 수 없다.



## 용어 사전

| 한글명 | 영문명 | 설명 |
| --- | --- | --- |
|  |  |  |

## 모델링
