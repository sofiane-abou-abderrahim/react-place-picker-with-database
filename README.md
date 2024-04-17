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

## 4. Using async / await

1. use `async` / `await` inside `useEffect()` by creating a `fetchPlaces()` function in `AvailablePlaces.jsx`
2. remove the old code

## 5. Handling Loading States

1. show some loading text whilst we are waiting for the data to arrive in case of bad network in `AvailablePlaces.jsx`
2. inside of `Places.jsx`, accept the `isLoading` & `loadingText` props
3. use these props to show some special output
4. control the `isLoading` prop dynamically depending on the progress of the HTTP request
5. add a new `isFetching` state to manage the loading state when fetching the data in `AvailablePlaces.jsx`

## 6. Handling HTTP Errors

1. handle the error response in `AvailablePlaces.jsx`
   1. with help of the `response.ok` property
   2. `throw` an `Error` & wrap the code with `try` / `catch` to prevent the application from crashing
   3. add an `error` state & use it to update the UI in case of error by rendering the `Error.jsx` component
2. replace the `Error.jsx` component by `ErrorMessage.jsx` to avoid conflict with the `Error` class name

## 7. Transforming Fetched Data

1. fetch the user's location before setting the available places with help of the `navigator` object in `AvailablePlaces.jsx`
2. sort the available places by calling `sortPlacesByDistance` from `loc.js`
3. set the `sortedPlaces` as the available places `setAvailablePlaces` inside of the `navigator` function
4. since you can't to use `await` on `navigator`, `setIsFetching` has to be moved elsewhere because it will be called too early
   1. move `setIsFetching(false)` into the `navigator` callback function after setting the `setAvailablePlaces(sortedPlaces)`
   2. call it again after setting the `error` if we have one

## 8. Extracting Code & Improving Code Structure

1. create a helper file named `http.js` & place the data fetching code from `AvailablePlaces.jsx` inside of it
2. use this `fetchAvailablePlaces` function in `AvailablePlaces.jsx`
