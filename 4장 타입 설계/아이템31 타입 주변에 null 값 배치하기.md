# 아이템31 타입 주변에 null 값 배치하기

### Q1. 다음 코드에서 어떤 문제가 발생할 수 있고 어떻게 해결할 수 있을까요? (경민)

```ts
type User = {
  id: number;
  name: string;
  email: string | null;
};

function getCachedUser(id: number): User | null {
  return id === 1 ? { id: 1, name: "Alice", email: null } : null;
}

function fetchUserFromAPI(id: number): User {
  return { id, name: "Bob", email: `bob${id}@example.com` };
}

function getUser(id: number): User {
  return getCachedUser(id) || fetchUserFromAPI(id);
}

function sendEmail(user: User) {
  console.log(`Sending email to: ${user.email.toUpperCase()}`);
}

const user = getUser(1);
sendEmail(user);
```
- getUser를 호출한 객체 안에 있는 email 속성이 Null일 수 있다
- 타입 가드
  - user의 타입을 체크해서 sendEmail을 호출할 때 분기
- 태그된 유니온 타입을 사용한다

### Q2. 다음  두 코드의 차이점을 설명후 어떤 코드가 더 나은 코드인지 선택해주세요? (수영)
```ts
class UserPostsA {
    user: UserInfo | null;
    posts: Post[] | null;

    constructor() {
        this.user = null;
        this.posts = null;
    }

    async init(userId: string) {
        return Promise.all([
            async() => this.user = await fetchUser(userId),
            async() => this.posts = await fetchPostsForUser(userId)
        ])
    }

    getUserName() {
        return this.user.name
    }
}

class UserPostsB {
    user: UserInfo;
    posts: Post[];

    constructor(user:UserInfo, posts:Post[]) {
        this.user = user;
        this.posts = posts;
    }

    static async init(userId: string) Promise<UserPosts> {
        const [user, posts] = await Promise.all([
            fetchUser(userId),
            fetchPostsForUser(userId)
        ]);

        return new UserPosts(user, posts);
    }

    getUserName() {
        return this.user.name;
    }
}
```
- 아래가 더 낫다!
- 차이점
  - 첫번째 코드는 user랑 post가 둘 다 null 되거나 하나만 null이거나 둘다 null이 아닐 수 있다는 문제가 있다.
  - 두번째 코드는 Promise.all로 user랑 post 타입 자체가 null 타입을 허용하지 않는다. (두개의 값이 한번에 결정된다)
---
참고)
첫번째 함수의 경우, 비동기 함수가 실행 자체가 되지 않는다.
이유: 
배열 안에는 async () => {} 형태의 **비동기 함수 정의(람다 함수)**가 들어가 있고, 람다 함수는 실행된 게 아니라 "함수 참조"일 뿐이다
Promise.all([...])은 배열 안의 요소들이 Promise 객체이길 기대하지만, 현재 배열에는 Promise가 아니라 "함수"가 들어가 있음.

### Q3. 두 개 이상의 비동기 함수를 사용하여 클래스의 속성값을 초기화할 때, 초기화하는 값이 null이 아니게 하기 위해 어떤 방법을 사용할 수 있나요? (유진)
- await - Promise.all을 사용해서 값을 같이 받도록 하고, null 체크도 따로 한다.
