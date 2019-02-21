# What is Redux

For browser state management

Provides predicable state management using `actions` and `reducers`



### `actions`

> Describe something has (or should) happen, but didn't say how

```react
//JS object with 2 properties or more (type (required), payload (optional, data))
{
  type: 'CREATE_TODO',
  payload: 'Build my first Redux app'
}
```



### `reducer`

> Pure function take takes the previous state and an action and returns the new state
>
> Reducers handle state transitions, but they must be done synchronously

```react
//sometime it returns the previous state
(state, action) => state

//sometimes it computes new state
(state, action) => state + action.payload

const counter = (state = 0, action) => {
  switch (Action.type) {
    case 'INCREMENT':
    	return state + 1;
    	
    case 'DECREMENT':
    	return state - 1;
    	
   	default:
   		return state;
  }
};
```

*All reduces will be invoked when an action is dispatched* [Here](https://stackoverflow.com/questions/33590579/all-reducers-will-be-invoked-when-an-action-is-dispatched?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)



### `mapStateToProps`

```react
const mapStateToProps = state => ({
    user: state.user
})
```



### `mapDispatchToProps`

```react
import { getSystemLandscape, getSystemData } from 'actions/getSystemLandscape';

function mapDispatchToProps() {
    return {
        getSystemLandscape,
        getSystemData
    }
}
```



### [`connect`](https://www.youtube.com/watch?v=l2IOqeubsBw)

> To pass data down multiple levels (via props is a pain), use `connect` to inject the data from the store into the component
>
> ```react
> export default connect(mapStateToProps, mapDispatchToProps())(MyComponent);
> ```



### [`dispatch`](https://roclv.gitbooks.io/redux-getting-started/content/06.redux-store-methods-getstate-dispatch-and-subscribe.html)

> Dispatch actions to change the state of your application
>
> All reducers are called

```react
<button onClick={() => dispatch({ type: 'INCREMENT' })}>
	Increment
</button>

dispatch({ type: constants.GETTING_PROGRAM_DUMPS });
dispatch(showAppBusy());
```



### `Subscribe`

> Lets you register a callback that the Redux store will call any time an action has been dispatched



Example

```
const Posts = ({isFetching, allPosts}) => (
  <div>
    {/* access isFetching, allPosts directly */}
  </div> 
)

connect(
  state => state.posts
)(Posts)
```





## About Async

### React handles asynchronous in synchronous way

1. Synchronously dispatch the increment
2. `reducer` will pick that up & increment

```react
<button onClick={() => dispatch({ type: 'INCREMENT' })}>
	Increment
</button>
```



### Update event after a period time after certain event

> Use `middleware` to manage asyn/side effects
>
> > Sits between your application and the redux store so any of the actions dispatch will go through the middleware either before or after they reach the reducer, where middleware controls which order
> >
> > `middleware` uses `callbacks` and `promises` (ability to do complex async stuff)



#### `callbacks`

> most primitive way in JS to handle async

```react
fetchSomeData((error, data) => {
  if (!error) {
    dispatch({ type: 'HERES_THE_DATA', data});
  }
});
```

> 1. Call a function passing it a callback, when the data comes back Bom



##### callback hell

> 1. Do async & do something else async when done
> 2. Run in parallel and do something else when finish

```react
fetchSomeData((error, data) => {
  if (!error) {
    dispatch({ type: 'HERES_THE_DATA', data});
   
	fetchSomeData((error, data) => {
  	  if (!error) {
        dispatch({ type: 'HERES_THE_DATA', data});
        
        fetchSomeData((error, data) => {
  	      if (!error) {
            dispatch({ type: 'HERES_THE_DATA', data});
          }
        });
      }
    });
  }
});
```



#### [Promise](https://developers.google.com/web/fundamentals/primers/promises)

> when provide call back to the promise, if your return another promise you can change them horizontally
>
> 1. Fetch data for the given ID
> 2. Fetch more data with the parent ID
> 3. Turning that new promise 

```react
fetchSomeDate(id)
  .them(data => {
     dispatch({ type: 'HERES_THE_FIRST_CALL_DATA', data});
     return fetchSomeData(data.parentId);
  })
  .them(data => {
     dispatch({ type: 'HERESE_SOME_MORE', data});
     return fetchSomeData(data.parentId);
  })
  .them(data => {
     dispatch({ type: 'OKAY_IM_DONE', data});
  })
```



#### Async/Await

```react
const makeRequest = async () => {
  console.log(await getJSON())
  return "done"
}

makeRequest()
```



#### [Async/Await VS Promises](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9)



## How

**Goal: To call the following API**

`http://localhost/api/v1/index.php/accounts/1/hourly?cmd=json&table=rtemetadata&filterstr=[]&res=3600&datestr=today&index=0`

1. Create a function to call the API

   ```react
   getProgramDumps(data) {
           const urlParams = {
               table: 'rtemetadata',
               datestr: 'today',
           };
           //cmd=json&table=rtemetadata&filterstr=[]&res=3600&datestr=today&index=0

           const opts = {
               method: 'GET',
               url: this.withAccount('/hourly'),
               urlParams: urlParams
           };
           return this.callApi(opts, false);
       }
   ```

2. Create constants in `constant.js`

   ```react
   const GETTING_PROGRAM_DUMPS = 'GETTING_PROGRAM_DUMPS';
   const GOT_PROGRAM_DUMPS = 'GOT_INCIDENT_OCCURRENCES';
   const GOT_PROGRAM_DUMPS_ERROR = ' GOT_PROGRAM_DUMPS_ERROR';

   const constants = {
       GETTING_PROGRAM_DUMPS,
       GOT_INCIDENT_OCCURRENCES,
       GOT_PROGRAM_DUMPS_ERROR
   }
   ```

3. Create an action

   ```react
   import constants from 'actions/constants';
   import { showAppBusy, hideAppBusy } from 'actions/spinner';
   import { druidapi } from 'service/druidapi';
   import { commonCheckError } from 'actions/commonCheckError';

   export const getProgramDumps = data => (dispatch, subscribe) => {
       dispatch({ type: constants.GETTING_PROGRAM_DUMPS });
       dispatch(showAppBusy());
       
       const action = async () => {
           let request = druidapi.getProgramDumps(data);
           let success = {
               type: constants.GOT_PROGRAM_DUMPS,
               callbacks: [() => hideAppBusy()]
           };
           let error = {
               type: constants.GOT_PROGRAM_DUMPS_ERROR,
               callbacks: [() => hideAppBusy()]
           };
           dispatch(commonCheckError(request, success, error));
       }
       action();
   }
   ```

4. Create a reducer

   ```react
   import constants from 'actions/constants';

   export default function getProgramDumps(state = initialState, action) {
       switch (action.type) {
           case constants.GETTING_PROGRAM_DUMPS:
               return { ...state, isFetching: true };
           case constants.GOT_PROGRAM_DUMPS:
               return { ...state, isFetching: false };
           case constants.GOT_PROGRAM_DUMPS_ERROR:
               return { ...state };
       }
   }
   ```

**In your component**

1. `import { getProgramDumps } from 'actions/getProgramDumps';`
2. ​



# Terminology

### AJAX



### Pure function

Same input always gives the same output





