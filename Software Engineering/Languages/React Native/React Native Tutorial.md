# [Setup](https://facebook.github.io/react-native/docs/running-on-device.html#running-on-device)

1. Go to your desired folder and run`react-native init AwesomeProject`

2. Run emulator: Android Studio → Tools → AVD Manager → `PLAY`

3. OR enable the `Developer options` 

   * **Settings** → **About phone**
   * Tap the `Build number` row at the bottom seven times.
   * Go back to **Settings** → **Developer options** to enable "USB debugging"
   * Plug-in the phone

   > Check that your device is properly connecting to ADB, the Android Debug Bridge, by running `adb devices`.

4. At project: run `react-native run-android`



### [Connecting to the development server](https://facebook.github.io/react-native/docs/running-on-device.html#connecting-to-the-development-server)



### Using native sdks in react native android

> 8 lines of code split in two files (header file & module implementation file)
>
> 1. Create two native files for our bridge (between React & native SDK)
> 2. PaymillBridge.h



### [create-react-native-app VS create-native init](https://forum.freecodecamp.org/t/difference-between-create-react-native-app-and-react-native-init-app/103609/2)

> `init` command:
>
> Installs all the necessary components it needs and starts up the environment to start developing in react-native.
>
> You’ll have full control over the native code compilation process.

> `create-react-native-app` 
>
> Encapsulated and curated bundle of developer tools designed for bootstrapping projects and helping beginners learn the react-native without having to deal with all the tedious configuration usually associated with creating a React project

> create-react init = create-react-native-app + npm run eject
>



### [AppRegistry VS export](https://stackoverflow.com/questions/44609520/why-cant-you-have-two-appregistry-registercomponent-lines)

Parent (1 file) `AppRegistry.registerComponent('someProject', () => Project);`

Children(components)`export default Header;`



# Debugging

### Refresh

* `R` key twice
* select `Reload` from the Developer Menu (`Ctrl + M`) to see your changes
* `console.log()`  OR `debugger`  using Debug mode in menu 




# Error

### [SDK Build Tools revision (23.0.1) is too low for project](https://github.com/oblador/react-native-keychain/issues/68) 

> Add the following to my root build gradle `android/build.gradle`
>
> Forces all the submodules to use the specified `compileSdkVersion` and `buildToolsVersion`

```
subprojects {
    afterEvaluate {project ->
        if (project.hasProperty("android")) {
            android {
                compileSdkVersion 25
                buildToolsVersion '25.0.0'
            }
        }
    }
}
```



# React Native Fun

### Props VS State

`props`: set by the parent and they are fixed throughout the lifetime of a component

`state`: data that is going to change



### *Using Props

```react
const Album = (props) => {
}

const Album = ({ album }) => {
  const { title, artist, thumbnail_image } = album;
}
```



## *Functions

```react
const AlbumList = () => {
  return (
  	<View>
  		<Taxt></Text>
  	</View>
  )
};
```

```react
const AlbumList = () => (
  	<View>
  		<Taxt></Text>
  	</View>
);
```



## Class

### [Named export VS Default](https://stackoverflow.com/questions/31852933/why-es6-react-component-works-only-with-export-default)

```react
export class Template {}
export class AnotherTemplate {}

import {Template, AnotherTemplate} from './components/templates'
```

```react
export default class Template {}
export class AnotherTemplate {}

import Template,{AnotherTemplate} from './components/templates'
```



### Calling Component (use *this.props*)

```react
import ...

class Greeting extends Component {
  render() {
    return (
      <Text>Hello {this.props.name}!</Text>
    );
  }
}

export default class LotsOfGreetings extends Component {
  render() {
    return (
      <View style={{alignItems: 'center'}}>
        <Greeting name='Rexxar' />
        <Greeting name='Jaina' />
        <Greeting name='Valeera' />
      </View>
    );
  }
}

// skip this line if using Create-React-Native-App
AppRegistry.registerComponent('AwesomeProject', () => LotsOfGreetings);
```



### Class with Constructors & methods

> When setState is called, BlinkApp will re-render its Component

```react
class Blink extends Component {
  constructor(props) {
    super(props);
    this.state = {showText: true};

    // Toggle the state every second
    setInterval(() => {
      this.setState(previousState => {
        return { showText: !previousState.showText };
      });
    }, 1000);
  }

  render() {
    let display = this.state.showText ? this.props.text : ' ';
    return (
      <Text>{display}</Text>
    );
  }
}

export default class BlinkApp extends Component {
  render() {
    return (
      <View>
        <Blink text='I love to blink' />
      </View>
    );
  }
}
```

### *Lifecycle Methods (auto call)

```react
componentWillMount() {	//will not run when re-render
}
```



## Functions VS Class

![Function VS Class](D:\Dropbox\My Document\md\JS\React Native\Img\Function VS Class.png)



### `maps` (for array)

```react
renderAlbum(){
  return this.state.albums.map((album,index) => <Text key={index}>{album.title}</Text>)
}
```



### props.children

```react
//In other component
<Card>
	<Text>{props.album.title}</Text>
</Card>

//In Card.js
<View>
	{props.children}
</View>
```



## HTTPS

```react
state = {albums: []};

axios.get('https://rallycoding.herokuapp.com/api/music_albums')
			.then(response => this.setState({ albums: response.data}));
```



## styles

```react
<Text style={styles.red}>just red</Text>

const styles = StyleSheet.create({
  bigblue: {
    color: 'blue',
    fontWeight: 'bold',
    fontSize: 30,
  },
  red: {
    color: 'red',
  },
});
```

```react
<Text style={red}>just red</Text>

const styles = {
  red: {
    color: 'red',
  },
};
```



### [flex](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

```react
<View style={{flex: 1}}> //height: 300px
  <View style={{flex: 1, backgroundColor: 'powderblue'}} />
  <View style={{flex: 2, backgroundColor: 'skyblue'}} />
  <View style={{flex: 3, backgroundColor: 'steelblue'}} />
</View>
```

### flexDirection

```react
<View style={{
    flex: 1,
    flexDirection: 'column',         //column, center
    justifyContent: 'space-between', //space-between, row, flex-end
    alignItems: 'center',            //flex-start, center
  }}>
  <View style={{width: 50, height: 50, backgroundColor: 'powderblue'}} />
  <View style={{width: 50, height: 50, backgroundColor: 'skyblue'}} />
  <View style={{width: 50, height: 50, backgroundColor: 'steelblue'}} />
</View>
```



## Components

### Textbox

```react
<TextInput
  style={{height: 40}}
  placeholder="Type here to translate!"
  onChangeText={(text) => this.setState({text})}
/>
```



### Button

```react
<Button
  onPress={this._onPressButton}
  title="Press Me"
  color="#841584"
/>
```



### Touchables 

> * capability to capture tapping gestures
> * display feedback when a gesture is recognized
> * do not provide any default styling

#### [**TouchableHighlight**](https://facebook.github.io/react-native/docs/touchablehighlight.html)

#### [**TouchableNativeFeedback**](https://facebook.github.io/react-native/docs/touchablenativefeedback.html)

#### [**TouchableOpacity**](https://facebook.github.io/react-native/docs/touchableopacity.html)

#### [**TouchableWithoutFeedback**](https://facebook.github.io/react-native/docs/touchablewithoutfeedback.html).

*pass a function to the `onLongPress` props of any of the "Touchable" components*



### *ScrollView (renders all elements)

```react
<ScrollView>	//props: pagingEnabled, maximumZoomScale, minimumZoomScale 
  --components--
</ScrollView>
```

> ****Include `flex: 1` in <View> @ index.js* 
>
> The ScrollView works best to present a small amount of things of a limited size.
>
> All the elements and views of a `ScrollView` are rendered, even if they are not currently shown on the screen.
>
> If you have a long list of more items that can fit on the screen, you should use a `FlatList` instead.



### FlatList (renders on-screen elements)

```react
<FlatList
  data={[
    {key: 'Devin'},
    {key: 'Jackson'},
    {key: 'James'},
    {key: 'Joel'},
    {key: 'John'},
    {key: 'Jillian'},
    {key: 'Jimmy'},
    {key: 'Julie'},
  ]}
    renderItem={({item}) => <Text style={styles.item}>{item.key}</Text>}
/>
```

> Displays a scrolling list of changing, but similarly structured, data.
>
> `FlatList` works well for long lists of data, where the number of items might change over time.
>
> Unlike the more generic [`ScrollView`](https://facebook.github.io/react-native/docs/using-a-scrollview.html), the `FlatList` only renders elements that are currently showing on the screen, not all the elements at once.



#### Data broken into logical sections

```react
<SectionList
  sections={[
    {title: 'D', data: ['Devin']},
    {title: 'J', data: ['Jackson', 'James', 'Jillian', 'Jimmy', 'Joel', 'John', 'Julie']},
  ]}
  renderItem={({item}) => <Text style={styles.item}>{item}</Text>}
  renderSectionHeader={({section}) => <Text style={styles.sectionHeader}>{section.title}</Text>}
/>
```



### [ViewPagerAndroid](https://facebook.github.io/react-native/docs/viewpagerandroid.html) 



### Connecting with API

```react
componentDidMount() {
  return fetch('https://facebook.github.io/react-native/movies.json')
    .then((response) => response.json())
    .then((responseJson) => {
      let ds = new ListView.DataSource({rowHasChanged: (r1, r2) => r1 !== r2});
      this.setState({
        isLoading: false,
        dataSource: ds.cloneWithRows(responseJson.movies),
      }, function() {
        // do something with new state
      });
    })
    .catch((error) => {
      console.error(error);
    });
}

render() {
  if (this.state.isLoading) {
    return (
      <View style={{flex: 1, paddingTop: 20}}>
        <ActivityIndicator />
      </View>
    );
  }

  return (
    <View style={{flex: 1, paddingTop: 20}}>
      <ListView
        dataSource={this.state.dataSource}
        renderRow={(rowData) => <Text>{rowData.title}, {rowData.releaseYear}</Text>}
      />
    </View>
  );
}
```











