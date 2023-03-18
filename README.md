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
