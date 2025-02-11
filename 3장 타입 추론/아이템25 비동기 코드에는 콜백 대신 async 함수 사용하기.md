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
    getUserId((id) => {
        getUserName(id, (name) => {
            console.log(`User: ${name}`);
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
    const id = 🔲;
    const name = 🔲;
    console.log(`User: ${name}`);
}

main();
```
