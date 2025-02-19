Pattern: Hard-coded API key or credential

Issue: -

## Description

Hard-coding API keys and credentials in source code creates serious security risks. These credentials can be exposed through source code leaks, accidental bundling, git history, or contractor access. Additionally, key rotation requires code changes and redeployment, making security management more difficult.

## Examples

Example of **incorrect** code:
```js
const AWS_ACCESS_KEY_ID = "AKIA1234X678C123B567";
const OPENAI_API_KEY = "sk_test_1234567890";
```

Example of **correct** code:
```js
const AWS_ACCESS_KEY_ID = process.env.AWS_ACCESS_KEY_ID;
const OPENAI_API_KEY = await getSecret("open-ai-api-key");
```