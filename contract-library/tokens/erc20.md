---
description: The one and only
---

# ERC20

The standard may be found at this address:

{% embed url="https://theethereum.wiki/w/index.php/ERC20\_Token\_Standard" %}

{% tabs %}
{% tab title="erc20.arl" %}
```ocaml
archetype erc20

constant name : string = "mytoken"

constant total : int = 1000
with {
  i0: total > 0
}

asset allowance {
    allowed : address;
    amount  : int;
} with {
    i2 : amount > 0;
}

asset tokenHolder identified by holder {
    holder     : address;
    tokens     : int;
    allowances : allowance collection;
} with {
    i1: tokens >= 0;
    i3: allowances.sum(the.amount) <= tokens;
} initialized by [
  { holder = caller; tokens = total; allowances = [] }
]

action dotransfer (dest : pkey of tokenHolder, value : int) {

  specification {
    p1 : before.tokenHolder.sum(tokens) = tokenHolder.sum(tokens);
    p2 : let some th = tokenHolder.get(dest) in
         let some bth = before.tokenHolder.get(dest) in
         th.tokens = bth.tokens + value
         otherwise true
         otherwise true;
    p3 : let some thc = tokenHolder.get(caller) in
         let some bthc = before.tokenHolder.get(caller) in
         thc.tokens = bthc.tokens - value
         otherwise true
         otherwise true;
    p4 : let some th = tokenHolder.get(dest) in
         forall t in tokenHolder,
         forall bt in before.tokenHolder,
         t.holder <> th.holder ->
         t.holder <> caller ->
         t.tokens = bt.tokens
         otherwise true;
  }

  failif {
    f0 : value < 0;
    f1 : tokenHolder.get(caller).tokens < value
  }

  effect {
    tokenHolder.update( tokenHolder.get(dest).holder, { tokens += value });
    tokenHolder.update( caller, { tokens -= value })
  }
}

```
{% endtab %}
{% endtabs %}

