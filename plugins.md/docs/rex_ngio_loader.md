## Introduction

Handles loading various URLs and tracking referral stats.

## Links

- [Plugin](https://rexrainbow.github.io/C3RexDoc/repo/rex_ngio_loader.c3addon)

## Dependence

- [rex_ngio_authentication](rex_ngio_authentication.md)

## Usage

[Sample capx](https://1drv.ms/u/s!Am5HlOzVf0kHmBHiKAl9VK8-iQ8s)

### Prepare

Put [rex_ngio_authentication](rex_ngio_authentication.md) into project, and set property `App id` and `AES key`.

### Host

Set the domain URL of this app in property `Host`.

### Open or get url of page

```mermaid
graph TB

Action["Action:Load Newground page<br>Action:Load more game<br>Action:Load author page<br>Action:Load official page<br>Action:Load referral"] --> ActionIsSuccess

subgraph Callback
ActionIsSuccess{Action<br>is success} --> |Yes| CondOnSuccess["Condition:On get url"]
ActionIsSuccess --> |No| CondOnError["Condition:On get url error"]
CondOnSuccess --- ExpResult["Expression:LastURL"]
CondOnError --- ExpError["Expression:ErrorMessage"]
end
```

1. open page or get url of page
    - `Action:Load Newground page`
    - `Action:Load more game`
    - `Action:Load author page`
    - `Action:Load official page`
    - `Action:Load referral`
2. Parameter `Operation`
    - `Open` : open a page in a new tab if success
    - `Get url` :
        - Success : `Condition:On get url`
            - `Expression:LastURL`
        - Error : `Condition:On get url error`
            - `Expression:ErrorMessage`

----

### Referral

Manage `Referral` in dashboard `API Tools`, `Referrals and Events`.