---
id: Provider lifecycle
aliases: []
tags:
  - riverpod
---

![alt provider-lifecycle](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*cjNno3XsK7pP3yKwyYL7gw.jpeg)

### 1. `init`

    We start using a provider by adding some kind of listener to it. Eg, `watch`, `listen`
    or `read` etc..
     If a an listener is added for the first time, then the provider will be `initilaized`.

### 2. `onCancel` and `onDispose`

    When all the listeners to a provider is removed it enters and paused/passive state(because no one is listening to it.), until a new listener is added. If the provider is an `autoDispose` provider then instead of entering to the passive or paused state it gets disposed of and all the resources used by the provider will be released

### 3. `onResume`

    This method will be called when a new listener is added to a provider that is in paused state

### 4. `refresh`

    When this method is called on a provider, then it will be disposed and reinitialized.
