---
title: "[공부 기록] Data Structure - Linked list and Hash table"
date: 2020-03-20 13:04:00
categories: DataStructure
---

## Linked list
`Linked list`는 크게 두 부분으로 나뉘어 있는 노드(객체)들의 연결 집합이다. 배열과 비교하였을 때 삽입, 삭제가 유연하지만 특정 값을 검색하거나 index로 접근하기에는 적합하지 않다.  
`Linked list`의 각 노드들은 값을 갖는 부분과 다음 노드의 주소를 갖는 두 부분으로 이루어져있다.   
![linked_list_node](https://user-images.githubusercontent.com/11348329/77137338-cd566100-6ab0-11ea-9463-dabcb36811f6.jpg)


여러 노드들을 연결하면 `Linked list`가 되는데 `Header`가 가리키는 노드는 첫 번째 노드가 되고 Null을 가리키는 노드는 마지막 노드가 된다.  
![simple_linked_list](https://user-images.githubusercontent.com/11348329/77137342-ce878e00-6ab0-11ea-897a-5b8e2b84ec77.jpg)


이러한 자료 구조를 `Linked list`라고 한다. 엄밀히 말하자면 `Simple linked list`(단순 연결 리스트)이다.  
다양한 종류가 더 있지만 이 포스트에서는 `Simple linked list`만 다룰 것이다.

### Linked list의 구성
| 내용 | 설명 |
| -------- | -------- |
| head | 맨 앞의 노드를 가리킨다. |
| tail | 맨 뒤의 노드를 가리킨다. |
| addToTail() | 맨 앞에 노드를 추가한다. |
| removeHead() | 맨 뒤의 노드를 삭제한다. |
| contains() | 특정한 값을 가진 노드가 있는지 검사한다. |

### Linked list를 어떤 논리로 구현할 수 있을까? (pseudo code)
![pseudo_code_linked_list](https://user-images.githubusercontent.com/11348329/77138987-87e96200-6ab7-11ea-8853-4f5aceaf5fb5.jpg)

## Hash table
`Hash table`이란 `key`와 `value`가 연결되어 있는 자료구조이다. `key`를 통해서 `value`에 접근할 수 있다. 내부적으로는 값을 저장하는 `bucket`의 개수가 `key`의 개수보다 적기 때문에 특정한 연산(`Hash function`)을 통해서 `Hash code`를 만들고(`Hashing`) 이것으로`index`를 만들어낸 후 그 `index`와 연결된 `bucket`에 값을 저장하게 된다. 한 `bucket`에는 여러 개의 값이 들어갈 수 있으며 이들은 `Linked list`형태로 저장이 된다. 이를 그림으로 표현하면 아래와 같다.
![hash_table](https://user-images.githubusercontent.com/11348329/77242434-c1e66f80-6c41-11ea-85f8-7081969fb188.jpg)

### Hash function
`key`값을 `Hash code`로 바꾸고 `index`를 만드는 함수.

`Hash function`의 종류  
SNEFRU : 1990년 R.C.Merkle에 의해 제안됬다. 128/254 bit 암호화 알고리즘이다.
N-HASH : 1989년 일본 NTT의 미야구치 등이 발표했다.  
MD4 : 1990년 Ron Rivest에 의해 개발된 MD5의 초기 버전으로서, 입력 데이터(길이에 상관없는 하나의 메시지)로부터 128비트 메시지 축약을 만듦으로써 데이터 무결성을 검증하는데 사용되는 알고리즘이다.  
MD5 : 1992년 Ron Rivest에 의해 개발. MD5는 널리 사용된 해시 알고리즘이지만, 충돌 회피성에서 문제점 이 있다는 분석이 있으므로 기존의 응용과의 호환으로만 사용하고 더 이상 사용하지 않도록 하고 있다.  
SHA : 1993년에 미국 NIST에 의해 개발되었고 가장 많이 사용되고 있는 방식이다. SHA1은 DSA에서 사용하도록 되어 있으며 많은 인터넷 응용에서 default 해시 알고리즘으로 사용된다. SHA256, SHA384, SHA512 는 AES의 키 길이인 128, 192, 256 비트에 대응하도록 출력 길이를 늘인 해시알고리즘이다.  
RMD : RMD128, RMD160는 RIPE 프로젝트의 RIPEMD나 MD4, MD5를 대신하기 위하여 디자인된 해시 알 고리즘이다. 128 비트의 출력을 내는 RMD128은 역시 충돌 회피성에서 문제점이 있다. RMD160은 효 율성은 떨어지지만 안전성을 높인 것으로 많은 인터넷 표준들에서 널리 채택되고 있다. RMD256과 RMD320은 각각 RMD128과 RMD160을 확장한 것이다.  
TIGER : TIGER는 64 비트 프로세서에 최적화되어서 64 비트 프로세서에서는 매우 빠르다.  

### Hashing
`Hash function`을 통해서 `Hash code`를 만드는 작업. 어떤 데이터를 복원이 불가능한 값으로 바꾸는 것. 이 점이 `암호화`와는 차이가 있다. `암호화`는 복호화가 되어야 하고 `Hashing`은 복구가 불가능하게 만든다.

### Hash Collision
`Hash Collision`이란 `hash function`을 통해서 `index`가 결정되고 그 값이 `bucket`에 들어가는 과정에서 한 `bucket`에 값이 몰려서 들어가게 되는 경우를 `Hash Collision`이라고 부른다. 그래서 좋은 `Hash function`은 `index`값이 골고루 나와야 한다. 이를 해결하기 위해서 다양한 방법이 적용되고는 하는데 아래와 같다.

#### 1. Chaining (체이닝)
충돌이 발생하면 `Linked list`에 삽입하여 해결. 한 `bucket`에 여러 데이터를 넣을 수 있는 구조.
#### 2. Open addressing (개방 주소법)
충돌이 발생하면 빈 곳을 탐색하여 값을 넣고 해결. 한 `bucket`에 데이터 한 개만 들어가는 구조. `Linear probing`(선형 탐사), `Quadratic probing`(제곱 탐사), `double hashing`(이중 해싱), `rehashing`(재해싱) 등의 방법이 있다.

### Hash table의 구성
| 내용 | 설명 |
| -------- | -------- |
| insert() | 키와 데이터를 매칭하여 넣는다. |
| retrieve() | 키를 통하여 데이터를 찾는다. |
| remove() | 키를 통하여 데이터를 삭제한다. |

### Hash table을 어떤 논리로 구현할 수 있을까? (pseudo code)
![pseudo_code_hash_table](https://user-images.githubusercontent.com/11348329/77244220-1562b880-6c56-11ea-8e94-38bafbf18eff.jpg)

출처  
<https://hyeonstorage.tistory.com/259>  
<https://youtu.be/Vi0hauJemxA>  
<https://luyin.tistory.com/191>  
<https://ratsgo.github.io/data%20structure&algorithm/2017/10/25/hash/>  
<http://wiki.hash.kr/index.php/%ED%95%B4%EC%8B%9C%ED%95%A8%EC%88%98>  
