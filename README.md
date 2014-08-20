This is a simple web page that guides learners towards making
a JavaScript-based app that presents the user with an outfit they
can wear based on the weather forecast. It's intended for
potential use in the [hour of code][].

Affordances have been added that make it easier to debug the
app's code in a live-reload environment like [Thimble][] and
[JS Bin][].

## API

### Data Types

Functions in the API deal with `forecast` objects that have the following
properties:

* `city` is a string that represents the city being forecast, e.g.
  `"New York City"`.
* `date` is a Date object representing the date and time for which the
  forecast is for. It is usually within 3 hours of the current time.
* `humidity` is a number describing the humidity, e.g. `83`.
  **TODO: What units are these measured in?**
* `next` is an optional property that points to another `forecast`
  object, which represents the forecast 3 hours from `date`. If no such
  forecast exists, this value will be undefined.
* `temp` is a number representing the temperature in Farenheit.
* `weather` is a string describing the weather conditions. It is
  one of `"clear"`, `"partly cloudy"`, `"mostly cloudy"`,
  `"raining"`, `"thunderstorming"`, `"snowing"`, and `"misty"`.

### Functions

Learners are expected to implement two global JavaScript functions that
comprise the core "business logic" of the app:

**getForecastWords**(*forecast*)

This function returns a string describing the forecasted weather
conditions, e.g. `"37F and cloudy"`.

**getForecastOutfit**(*forecast*)

This function returns a URL string that points to an image of a
suggested outfit to wear based on the given forecast, e.g. 
`"http://example.org/summer-outfit.jpg"`.

## Limitations

The current implementation is only localized to English and Farenheit,
and there's no easy way to use Celsius or another language.

It's not easy to change the HTML, templates, or CSS for the app.

`getForecastOutfit` can currently only return a URL to an image, but it
should be possible to dynamically construct an outfit using a Canvas object.
This may also require an asynchronous callback.

## Deployment

To deploy to an HTML page that only includes absolute links to
its sub-resources, run `node bin/export.js` from the command line
and pipe its output somewhere.

For example, on OS X, running `node bin/export.js | pbcopy` will put
the resulting HTML in your clipboard, at which point you can
paste it into Thimble or JS Bin.

If you want to use a different base URL for the sub-resources than
the default of `http://toolness.github.io/weather-outfit-fun/`, you
can supply it as an argument to the export script, e.g.
`node bin/export.js http://example.org/weather-outfit/`.

  [hour of code]: http://csedweek.org/
  [Thimble]: https://thimble.webmaker.org/
  [JS Bin]: http://jsbin.com/
