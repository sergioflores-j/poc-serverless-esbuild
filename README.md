# POC serverless-esbuild + serverless-offline

Watch mode is problematic with serverless-offline v9+. It has been introduced a new way for running the handlers with Worker Threads and the support for HMR has been dropped.

This is a poc repository to set a base working template with the best versions as possible.

Steps to reproduce:

1. Install dependencies
```
yarn
```

2. Start server
```
yarn start
```

3. Perform an API call to the `http://localhost:3000/dev/hello` route.
PS: you can use the `api.rest` file using the `Rest Client` extension in VSCode.

4. Change some code. E.g. the console log.
> If we check the `.esbuild./.build` folder, we can see that the handler code is correctly (re)built with ESBuild.

5. Perform the API call again. 

## Noticed behavior

Expected: The code change should be visible in the new run.

Current: New code runs, due to running with sls-offline v8.
