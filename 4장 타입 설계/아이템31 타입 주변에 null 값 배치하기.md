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
            async() -> this.posts = await fetchPostsForUser(userId)
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
            fetch(userId), 
            fetchPostsForUser(userId)
        ]);

        return new UserPosts(user, posts);
    }

    getUserName() {
        return this.user.name;
    }
}
```

