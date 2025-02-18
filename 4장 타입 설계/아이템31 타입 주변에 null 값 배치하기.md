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
