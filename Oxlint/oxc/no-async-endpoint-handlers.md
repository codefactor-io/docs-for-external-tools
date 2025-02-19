Pattern: `async` Express handler

Issue: -

## Description

Express versions before 5.0 do not automatically handle Promise rejections from `async` handlers. Unhandled rejections will crash the server instead of being passed to the error handler.

## Examples

Example of **incorrect** code:
```javascript
app.get("/users", async (req, res) => {
  const users = await db.getUsers();
  res.json(users);
});

router.use(async (req, res, next) => {
  req.user = await getUser(req.params.id);
  next();
});
```

Example of **correct** code:
```javascript
app.get("/users", (req, res, next) => {
  db.getUsers()
    .then(users => res.json(users))
    .catch(next);
});

const asyncHandler = fn => (req, res, next) =>
  Promise.resolve(fn(req, res, next)).catch(next);
```