# [clj-http-hystrix "0.1.0-SNAPSHOT"]

A Clojure library to wrap clj-http requests as [hystrix](https://github.com/Netflix/Hystrix) commands whenever a request options map includes `:hystrix/...` keys.

## Usage

When you start your app, add:

```clj
(clj-http-hystrix.core/add-hook)
```

Whenever you make an http request, add one or more of the hystrix-clj options to your options map:

```clj
(http/get "http://www.google.com" {:hystrix/command-key     :default
                                   :hystrix/fallback-fn     default-fallback
                                   :hystrix/group-key       :default
                                   :hystrix/threads         10
                                   :hystrix/queue-size      5
                                   :hystrix/timeout-ms      600})
```
Any values not supplied will be set to their default values as above.


Requests with no hystrix-related keys wont use hystrix.

## License

Copyright © 2014 Joe Littlejohn

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
