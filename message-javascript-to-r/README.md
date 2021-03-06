# Send a message from JavaScript (client) to R (server)

In some shiny applications you may want to send a value from JavaScript to the R server. This can be useful in a variety of applications, for example if you want to capture a mouse click or a keyboard press of the user and tell R about it. This example shows how this is done.

The way this kind of communication is supported in Shiny is by using inputs. Usually when you think of a Shiny input you think of an input control (such as a `textInput` or a `sliderInput`) that gets its value updated when the user interacts with it, and you can access its value in Shiny inside a reactive context such as an `observe()` or a `reactive()` statement using the `input` list. But in order to send a value from JS to R, we can assign a value to an arbitrary input name from JavaScript, and then in Shiny we can use that input inside any reactive contexts as if it was a regular "native" input.

More specifically, in order to send a value from JavaScript to Shiny, there are two steps: first, in your JavaScript code you need to call `Shiny.onInputChange(name, value)` where `name` is the input name that will be used in Shiny and `value` is any JavaScript object that will be passed to Shiny. Then in your Shiny app you can use use `input$name` (replace `name` with the actual name you used) and it will hold the updated value that was assigned to it in JavaScript. While this may sound complicated, looking at the example code shows how simple this is.

To send a message in the other direction (from R to JavaScript), see [Send a message from R to JavaScript](../message-r-to-javascript).

[See a real shiny app where I used this concept](http://daattali.com/shiny/cfl/)