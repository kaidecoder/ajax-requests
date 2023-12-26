### The XMLHttpRequest API

Sometimes, especially in older code, you'll see an API called XMLHttpRequest (often abbreviated as "XHR") used to make HTTP requests. This predated Fetch, and was really the first API widely used to implement AJAX. We recommend you use Fetch if you can: it's a simpler API and has more features than XMLHttpRequest.  This is what an XMLHttpRequest  looks like: 


const request = new XMLHttpRequest();

try {
  request.open("GET", "products.json", true);

  request.responseType = "json";

  request.addEventListener("load", () => initialize(request.response));
  request.addEventListener("error", () => console.error("XHR error"));

  request.send();
} catch (error) {
  console.error(`XHR error ${request.status}`);
}
There are five stages to this:

Create a new XMLHttpRequest object.
Call its open() method to initialize it.
Add an event listener to its load event, which fires when the response has completed successfully. In the listener we call initialize() with the data.
Add an event listener to its error event, which fires when the request encounters an error
Send the request.
We also have to wrap the whole thing in the try...catch block, to handle any errors thrown by open() or send().

Hopefully you think the Fetch API is an improvement over this. In particular, see how we have to handle errors in two different places.

Reference https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Fetching_data