# Shimmer

A Gleam library for interacting with the Discord API

## Basic Example

```gleam
import gleam/io
import shimmer
import shimmer.{on_message, on_ready}

pub fn main() {
  let handlers =
    shimmer.Client(token: "TOKEN", intents: 0, handlers: handlers)
    |> on_ready(fn() { io.print("Ready") })
    |> on_message(fn(message) { io.print("Message Received!") })
    |> shimmer.handlers_from_builder

  let client =
    shimmer.new("TOKEN", 0, handlers)
    |> shimmer.connect

  erlang.sleep_forever()
}
```

## Notes

- Currently, we bundle [nerf](https://github.com/lpil/nerf), this will be removed once this [pull request](https://github.com/lpil/nerf/pull/1) is merged.