# 아이템25 비동기 코드에는 콜백 대신 async 함수 사용하기

### Q1. 다음 네모를 채워주세요. (경민)

```ts
/// ASIS
function getUserId(callback: (id: number) => void) {
    setTimeout(() => {
        callback(1);
    }, 1000);
}

function getUserName(id: number, callback: (name: string) => void) {
    setTimeout(() => {
        callback("Alice");
    }, 1000);
}

function main() {
    let userId: number;
    let userName: string;

    getUserId((id) => {
        userId = id;
        getUserName(userId, (name) => {
            userName = name;
            console.log(`User ID: ${userId}, User: ${userName}`);
        });
    });
}

main();

/// TODO
function getUserId(🔲): 🔲 {
    return new Promise((resolve) => {
        setTimeout(() => resolve(1), 1000);
    });
}

function getUserName(🔲): 🔲 {
    return new Promise((resolve) => {
        setTimeout(() => resolve("Alice"), 1000);
    });
}

async function main() {
    const userId = 🔲
    const userName = 🔲
    console.log(`User ID: ${userId}, User: ${userName}`);
}

main();
```

답:

```ts
/// TODO
function getUserId(): Promise<number> {
  return new Promise((resolve) => {
    setTimeout(() => resolve(1), 1000);
  });
}

function getUserName(): Promise<string> {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Alice"), 1000);
  });
}

async function main() {
  const userId = await getUserId();
  const userName = await getUserName();
  console.log(`User ID: ${userId}, User: ${userName}`);
}

main();
```

### Q2. 프로미스 대신 async/await을 사용할 때 얻을 수 있는 이점을 말해주세요. (유진)

가독성이 좋아지고 코드가 간결해짐. <br/>
예상치 못하게 작동하는 반동기를 줄이고 항상 비동기로 작동하게 할 수 있다. <br/>
async 함수는 항상 프로미스를 반환하도록 강제함. 그래서 비동기로 작동하게 함.
