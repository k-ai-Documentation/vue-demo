# vue-demo-search

## Introduce
This project is a demo for vue3, which contains 'search' function with sdk-js. This demo will show you how to use sdk-js in vue3.

## Before setup
[vue-demo-search](https://github.com/k-ai-Documentation/vue-demo-search).

And your directory should like this:
```
|-your root directory
    |-vue-demo-search
```
open terminal and run
```bash
cd vue-demo
```
Add fill your keys in .env.development file.

If you are using SaaS version, you need 3 keys(organizationId, instanceId, apiKey).

If you are using Premise version, you need host and api key(optional).

See More about SaaS and Premise version in [here](https://github.com/k-ai-Documentation/sdk-js#usage-guide).
```
# if you are using saas 
VUE_APP_ORGANIZATION_ID = ''
VUE_APP_INSTANCE_ID = ''
VUE_APP_API_KEY = ''

# if you are using version premise. You must need host, but api key is optional, depends on your enterprise settings. 
VUE_APP_HOST = ''
VUE_APP_API_KEY = ''
```

## Installation
```bash
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

# How to use [sdk-js](https://github.com/k-ai-Documentation/sdk-js)

+ make sure you have installed sdk-js and vue-demo.
```
npm install
```
+ check in your package.json and node_modules, sdk-js should be installed.

+ check .env.development has VUE_APP_ORGANIZATION_ID, VUE_APP_INSTANCE_ID and VUE_APP_API_KEY.

+ in your vue file, import sdk-js.
```
import { KaiStudio } from "kaistudio-sdk-js";
```
if your are using typescript, you need to define searchResult.
```
import type { SearchResult } from 'kaistudio-sdk-js/modules/Search';
```
+ Create your sdk instance
````
let sdk = new KaiStudio({ organizationId: process.env.VUE_APP_ORGANIZATION_ID , instanceId: process.env.VUE_APP_INSTANCE_ID, apiKey: process.env.VUE_APP_API_KEY });
````

+ use it in your methods
```
async function searchRequest(){
    try {
        if(searchInput.value) {
            searchAnswer.value = null
            const request = await sdk.search().query(searchInput.value, "")
            searchAnswer.value = request
        }
    } catch(e) {
        console.error(e)
        return null
    }
}
```
