---
title: The Ethernaut (part 1)
tags: wargame blockchain
cover: /assets/images/ethernaut/the_ethernaut.png
mode: immersive
header:
  theme: dark
article_header:
  type: cover
  image:
    src: /assets/images/ethernaut/aaa@4x.png
---

# Level 0 - Hello Ethernaut
<p style="text-align:center;">
    <img class="image image--xl" src="/assets/images/ethernaut/lv0.png"/>
</p>

This level is tutorial to The Ethernaut and how to interact with the ABI (Application Binary Interface). As step 9 in the tutorial, we should look into level info by the `await contract.info()`.
```js
>> await contract.info()
"You will find what you need in info1()."
```
Change to `info1()`
```js
>> await contract.info1()
'Try info2(), but with "hello" as a parameter.' 
```
And continue following commands.
```js
>> await contract.info2("hello")
"The property infoNum holds the number of the next info method to call." 
>> (await contract.infoNum()).toString()
"42"
>> await contract.info42()
"theMethodName is the name of the next method."
>> await contract.theMethodName()
"The method name is method7123949."
>> await contract.method7123949()
"If you know the password, submit it to authenticate()." 
```

Now the goal is to find the password and then submit to authenticate. Check again so there is a function call name `password`. Just call it and submit the answer.

```js
>> await contract.password()
"ethernaut0" 
```

Accept the Authenticate transaction in Metamask and done level 0.