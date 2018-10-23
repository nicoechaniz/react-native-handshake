
# react-native-handshake

## Getting started

`$ npm install react-native-handshake --save`

### Mostly automatic installation

`$ react-native link react-native-handshake`

### Manual installation


#### Android

1. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import net.altermundi.rn_handshake.HandshakePackage;` to the imports at the top of the file
  - Add `new HandshakePackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-handshake'
  	project(':react-native-handshake').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-sd/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      compile project(':react-native-handshake')
  	```


## Usage
```javascript
import { Handshake } from 'react-native-handshake';

// TODO: What to do with the module?
```
  