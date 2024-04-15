# Data Fetching & HTTP Requests

## Sending & Receiving Data via HTTP

- How To Connect a Backend / Database
- Fetching Data
- Sending Data

# Steps

## 0. Starting Project & Dummy Backend API

1. run `npm install`
2. run `npm run dev`
3. create a `README.md` file

## 1. Preparing the App For Data Fetching

1. connect this React app with this dummy backend
2. write `cd backend` in the terminal
3. run `npm install` & run `node app.js` to run the backend
4. add a new `availablePlaces` state with an empty array as initial state in `AvailablePlaces.jsx`

## 2. How NOT To Send HTTP Requests (And Why It's Wrong)

1. use the `fetch` function to fetch the data from the backend API
2. you are not allowed to use the `await` & `async` keywords in a React component
3. call `setAvailablePlaces` inside of the `fetch` function to get back the data

## 3. Sending HTTP Requests (GET Request) via useEffect

1. use `useEffect` to fix this problem of infinite loop
2. make the image files available with help of `app.use(express.static('images'));` in the backend
3. send a request to for those image files to the backend in the frontend in `Places.jsx`
