# Scotty

A Haskell web framework inspired by Ruby's Sinatra, using WAI and Warp.

```haskell
{-# LANGUAGE OverloadedStrings #-}
import Web.Scotty

import Data.Monoid (mconcat)

main = scotty 3000 $ do
  get "/:word" $ do
    beam <- param "word"
    html $ mconcat ["<h1>Scotty, ", beam, " me up!</h1>"]
```

Scotty is the cheap and cheerful way to write RESTful, declarative web applications.

  * A page is as simple as defining the verb, url pattern, and Text content.
  * It is template-language agnostic. Anything that returns a Text value will do.
  * Conforms to WAI Application interface.
  * Uses very fast Warp webserver by default.

See examples/basic.hs to see Scotty in action. (basic.hs needs the wai-extra package)

    > runghc examples/basic.hs
    Setting phasers to stun... (ctrl-c to quit)
    (visit localhost:3000/somepath)

This design has been done in Haskell at least once before (to my knowledge) by
the miku framework. My issue with miku is that it uses the Hack2 interface
instead of WAI (they are analogous, but the latter seems to have more traction),
and that it is written using a custom prelude called Air (which appears to be an
attempt to turn Haskell into Ruby syntactically). I wanted something that
depends on relatively few other packages, with an API that fits on one page.

As for the name: Sinatra + Warp = Scotty.

Copyright (c) 2012 Andrew Farmer
