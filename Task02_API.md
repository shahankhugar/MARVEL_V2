# Task 02 — API

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is an API?

An API (Application Programming Interface) is a way for two programs to communicate with each other. When you want data from a server, you don't access the server directly — instead you make a request to an API endpoint, and the API sends back only the data you asked for.

A simple way to think about it: the API is like a waiter at a restaurant. You (the app) tell the waiter what you want, the waiter goes to the kitchen (the server), and brings back exactly what you ordered. You never enter the kitchen yourself.

---

## How an API call works

When you make an API call, your code sends an HTTP request to a URL called an endpoint. The server receives the request, processes it, and sends back a response — usually in JSON format.

JSON (JavaScript Object Notation) is just data formatted as key-value pairs, like a JavaScript object. For example, asking the SpaceX API for Falcon 9 returns something like:

```json
{
  "name": "Falcon 9",
  "height": { "meters": 70 },
  "mass": { "kg": 549054 },
  "engines": { "number": 9 },
  "cost_per_launch": 50000000,
  "success_rate_pct": 98
}
```

Your JavaScript then reads this and displays the values on screen — `data.name` gives "Falcon 9", `data.height.meters` gives 70, and so on.

---

## What I built

I built a SpaceX Rocket Explorer web app using the SpaceX public REST API. The app lets you select any SpaceX rocket from a dropdown and displays its full technical details — height, mass, engine count, cost per launch, success rate, first flight date, and an image.

The SpaceX API is a free public API that requires no API key. Anyone can call it directly from the browser.

---

## How the app works

The app makes two API calls.

The first call happens automatically when the page loads. It fetches the full list of rockets from `https://api.spacexdata.com/v4/rockets` and uses the response to fill the dropdown menu with rocket names. Each option stores the rocket's ID invisibly as its value.

The second call happens when you click the button. It takes the ID of whichever rocket you selected, appends it to the endpoint URL like `https://api.spacexdata.com/v4/rockets/{id}`, and fetches the full data for just that rocket. The response is then parsed as JSON and each field is injected into the corresponding HTML element on the page.

The entire logic is `async/await` based — `async` marks the function as one that will wait for a response, and `await` pauses execution until the `fetch()` call completes and the data comes back.

---

## Key concepts covered

**REST API** — an API where different URLs (endpoints) return different data. `/rockets` returns all rockets, `/rockets/{id}` returns one specific rocket.

**fetch()** — the built-in JavaScript function used to make HTTP requests from the browser.

**JSON** — the format APIs use to send data back. JavaScript can parse it directly with `.json()`.

**async / await** — how JavaScript handles tasks that take time, like waiting for a server response over the internet.

**DOM manipulation** — using `document.getElementById()` to find HTML elements and put data into them so the user can see the result.

---

## Applications of APIs

APIs are used everywhere in software. Weather apps, payment gateways like Razorpay, maps in Swiggy and Ola, login with Google — all of these work by calling APIs behind the scenes. In AI/ML, the same concept applies: when you use GPT or Gemini in an app, you're calling their API and getting a response back exactly like this.

---

## Links

**Done by me —** https://shahankhugar.github.io/MARVEL_V2/Basic_XAPI/

**Improved using AI —** https://shahankhugar.github.io/UVCE-MARVEL-AI-ML-001/
