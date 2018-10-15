# tkd-smoothies

> A Vue project using webpack.
> This project uses Materialize for basic styling, as the focus is on the Vue.js functionality rather than on the CSS.
We will endeavor in each commit to explain the code modifications contained within the commit. Each commit will build on the previous commits, until the fully functional app is completed.

## Important project note
This repo does not contain a critical directory and file, specifically the src/firebase/init.js file which contains code including the Firebase API key necessary to communicate with the backend database.
The code designated by **   ** is added to the code supplied by the Firebase setup process.

### Note for deployment to Firebase
Consult the file 'important-data.txt' for deployment instructions

```
**import firebase from 'firebase'**
**import firestore from 'firebase/firestore'**

// SUPPLIED BY FIREBASE
var config = {
  apiKey: "API_KEY_HERE",
  authDomain: "FROM_FIREBASE_SETUP",
  databaseURL: "FROM_FIREBASE_SETUP",
  projectId: "FROM_FIREBASE_SETUP",
  storageBucket: "FROM_FIREBASE_SETUP",
  messagingSenderId: "FROM_FIREBASE_SETUP"
};

**const firebaseApp = firebase.initializeApp(config)**
**firebaseApp.firestore().settings({ timestampsInSnapshots: true })**

// export firestore database
**export default firebaseApp.firestore()**
```

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
