Some personal notes

## Reducers

The reducer is going to control the state in the cartSlice

Accessing data from initial state:
We use `useSelector` to access the store (entire state of the application)

For example, for the Navbar, we are able to access the amount of items in the initial cart by running the following

```javascript
const amount = useSelector((store) => store.cart.amount);
```

## Actions

As we have imported redux toolkit, Immer is included. This allows us to create actions in one line:

```js
export const { clearCart } = cartSlice.actions;
```

To use the action we have created, we can use `useDispatch`

We can access the payload of the action, when we log it out it shows us the id of an item in this case. We can use this information to access and manipulate values

```js
const itemId = action.payload;
```

For logic invloving slices, these have to be done externally. For example, I tried adding logic to avoid the amount becoming negative, but this had to be done within the `onClick` call instead

## Async Thunk

Provided with the redux toolkit, this allows us to access api data.
Once we fetch it, it is returned in the form of a promise, so `fulfilled`, `pending` or `rejected`

We have to create scenarios for each of the possible outcomes. For example, in `cartSlice.js`

```js
extraReducers: {
    [getCartItems.pending]: (state) => {
      state.isLoading = true;
    },
    [getCartItems.fulfilled]: (state, action) => {
      state.isLoading = false;
      state.cartItems = action.payload;
    },
    [getCartItems.rejected]: (state) => {
      state.isLoading = false;
    },
  },
```
