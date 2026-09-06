## Callback
Callback is a function passed as an argument in another function.

```
function getData(dataId, getNextData) {
  setTimeout(() => {
    console.log(dataId);
    if(getNextData) {
      getNextData();
    }
  }, 2000);
}

// Callback
getData(1, () => {
  getData(2);
});

// Callback hell
getData(1, () => {
  getData(2, () => {
    getData(3, () => {
      getData(4)
    })
  })
});
```

> Callback hell is problem where nested callbacks are stacked below one another forming a pyramid type structure.

## Promise
Promise is an object is JS (resolve and reject are callbacks provided by JS).

Promise has 3 states:
1. pending
2. fulfilled
3. rejected

Promise chaining is done using (.then() & .catch())

```
let promise = new Promise((resolve, reject) => {
});

function getData(dataId, getNextData) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(dataId);
      resolve("success");
      if(getNextData) {
        getNextData();
      }
    }, 2000);
  });
}

getData(1)
  .then((res) => {
    return getData(2)
  })
  .then((res) => {
    console.log(res);
  });

// Promise Chaining
getData(1)
  .then((res) => {
    return getData(2)
  })
  .then((res) => {
    return getData(2)
  })
  .then((res) => {
    return getData(4)
  })
  .then((res) => {
    console.log(res);
  });

```

## Async - Await
Async function always returns a promise.
Await pauses the execution of its surrounding async function until the promise is settled.

```
function getData(dataId, getNextData) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(dataId);
      resolve("success");
    }, 2000);
  });
}

async function getAllData() {
  await getData(1);
  await getData(2);
  await getData(3);
  await getData(4);
}
```






