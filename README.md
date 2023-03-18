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
