# Lazy

{% code title="auction\_lazy.arl" %}
```ocaml
archetype auction_lazy

asset bid identified by incumbent {
  incumbent : address;
  val : tez;
}

variable deadline : date = 2019-01-01T00:00:00

action place_bid () {
  require {
    c1 : now < deadline;
  }
  effect {
    bid.add({ incumbent = caller; val = transferred })
  }
}

(*Users need to exhibit proof they are not the winner to reclaim their bid*)
action reclaim (witness : address) {
  require {
    c2 : now < deadline;
    c3 : (let bc = bid.get(caller).val in
          let bw = bid.get(witness).val in
          bc < bw);
  }
  effect {
    transfer bid.get(caller).val to caller
  }
}

specification {
  contract invariant s1 {
    forall b in bid, balance > b.val
  }
}

```
{% endcode %}

