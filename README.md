# POC serverless-esbuild + serverless-offline

Watch mode is problematic with serverless-offline v9+. It has been introduced a new way for running the handlers with Worker Threads and the support for HMR has been dropped.

This is a poc repository to check what are the possibilities, due to possible lack of (good) support for serverless v3 options when using serverless-offline v8.

Steps to reproduce:

1. Install dependencies
```
yarn
```

2. Start server
```
yarn sls offline start --verbose
```

3. Perform an API call to the `http://localhost:3000/dev/hello` route.
PS: you can use the `api.rest` file using the `Rest Client` extension in VSCode.

4. Change some code. E.g. the console log.
> If we check the `.esbuild./.build` folder, we can see that the handler code is correctly (re)built with ESBuild.

5. Perform the API call again. 

## Expected behavior

The code change should be visible in the new run.

## Current behavior

The code executed is still the old one.
