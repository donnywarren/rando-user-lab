# Random User App
_Introduction_
In this exercise, you will build a react app that fetches a random user from an api and displays the user information in a user detail component.  The user detail component will have a button for toggling less/more views of the user data

## Set up
- make a new react app with `create-react-app rando-user`
- `cd` into the app directory and install `axios`
- Clear out the boilerplate and add a header to the app component with a nice title for our random user app

## Fetch a User
- Add a button to the App component that when clicked calls a function `refreshUser`.  This will entail the following steps:
	- Write a method `refreshUser` in the App component
	- don't forget to `bind` it in the constructor
	- pass `fetchUser` to the `onClick` prop on the button
	- For now, just `console.log` a message inside fetchUser to make sure it works
- After verifying that the `refreshUser` button calls the `refreshUser` method (using a console.log statement), add a `services` directory
- Inside `services/` add a `rando_user.js` file
- Inside `rando_user.js` import axios, set a base url to "https://api.randomuser.me/"
- Also inside `rando_user.js` write an async function `fetchUser` that fetches a random user using the above url and returns the response
- Export `fetchUser` from the file
- Back in the App component, import `fetchUser`, and call it within a `componentDidMount` method.  Don't forget to make `componentDidMount` an `async` function and `await` the return value from `fetchUser`
- Add a `currentUser` state variable in the App component; it's initial value should be `null`.  Use setState to update `currentUser` with the user information returned by `fetchUser`.
- You can verify this is all working by either `console.log`ing `this.state.currentUser` from the App component or adding a line to the `render` method that looks like this: `<div>{JSON.stringify(this.state.currentUser)}</div>` That will spit out the raw JSON representation of the user data to the DOM.

## Display Some User Data

- Add a `components` directory, and inside `components`, add a `UserSummary` component.  Make it a class component
- `UserSummary` should take a single prop, `userData`.  Import it and use it inside the App component.  Pass `this.state.currentUser` to `UserSummary` as a `userData` prop, i.e., `<UserSummary userData={this.state.currentUser} />`
- Inside the `UserSummary` component, if the `userData` prop is null, render a message saying "there is no user data"
- *else* if UserData is not null, render the user's name, and email

## More or Less
- Inside `UserSummary`, add a state variable `showMore` with an initial value of `false
- Add a button to `UserSummary` that calls a method to toggle `showMore` to be true if is false and flip it to false if it is true.  Remember to use the version of `setState` that takes a callback, i.e., `setState(prevState => { ...`
- Adjust the component so that if `showMore` is true, then the user's name, email, street, city, state, and username are displayed.  If `showMore` is false, just show the name and email as before


### Bonus
- If `showMore` is true, display the user's medium picture as well.

- Add more to the `UserSummar` to display even more information about the user, or maybe track all the user's that have been fetched and display them in a UserList component
