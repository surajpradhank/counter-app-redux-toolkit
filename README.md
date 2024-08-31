# Architecture

![image](https://github.com/user-attachments/assets/4e5f6b94-08ba-447f-b187-66953b21f92e)


# Steps

## 1: Create a Redux Store

Import the **configureStore** API from Redux Toolkit

export const store = configureStore({
  reducer: {},
})

## 2: Provide the Redux Store to React

Once the store is created, we can make it available to our React components by putting a **React-Redux <Provider>** around our application 

import the store created in step-1
<Provider store={store}>
    <App />
</Provider>

## 3: Create a Redux State Slice

For creating a slice , we require below thing
 -> a *string name* to identify the slice
 -> an *initial state* value
 -> one or more *reducer functions* to define how the state can be updated.

Once a slice is created, we can export the generated Redux action creators and the reducer function for the whole slice.

    Ex- 
    export const  counterSlice = createSlice({
        initialState: 0,
        name: "Counter",
        reducers:{
            increment:(state) =>state + 1,
            decrement: (state) => state - 1
        },
    });
    export const {decrement, increment} = counterSlice.actions;
    export default counterSlice.reducer;

## 4 Add Slice Reducers to the Store

Import the reducer function from the counter slice and add it to our store. 
By defining a field inside the reducer parameter, we tell the store to use this slice reducer function to handle all updates to that state.

## 5 Use Redux State and Actions in React Components

We can use the React-Redux hooks to let React components interact with the Redux store. We can read data from the store with useSelector, and dispatch actions using useDispatch
