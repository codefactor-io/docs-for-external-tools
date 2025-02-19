Pattern: Sequential `await` in loop body

Issue: -

## Description

Using `await` within loops executes async operations sequentially, preventing potential parallelization. This can lead to significantly slower execution times when the operations could be run concurrently.

## Examples

Example of **incorrect** code:
```javascript
async function processUsers(users) {
  for (const user of users) {
    const userRecord = await getUserRecord(user);
    await processRecord(userRecord);
  }
}

async function processIds(ids) {
  ids.forEach(async id => {
    await processItem(id);
  });
}
```

Example of **correct** code:
```javascript
async function processUsers(users) {
  const userRecords = await Promise.all(
    users.map(user => getUserRecord(user))
  );
  await Promise.all(userRecords.map(record => processRecord(record)));
}

async function processIds(ids) {
  await Promise.all(ids.map(id => processItem(id)));
}
```