
# react-native-handshake

This simple module is intended to be used with the react-native-nsd module to send and receive handshake messages to/from other discovered peers.

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
import { DeviceEventEmitter } from 'react-native';

let HANDSHAKE_MESSAGE = "My cool message"


DeviceEventEmitter.addListener('handshakeServerStarted', function(e){
  console.log("handshakeServerStarted");
  console.log(e.port);
});

DeviceEventEmitter.addListener('handshakeServerStopped', function(e){
  console.log("handshakeServerStopped");
});

DeviceEventEmitter.addListener('peerPubKeyReceived', function(e){
  console.log("JS: peer public key received");
  console.log(e.key);
});

// Start the server. Will emit HANDSHAKE_MESSAGE to any client that connects 
Handshake.startServer(HANDSHAKE_MESSAGE);

// receive a Handshake message from a server/peer. Will emit a peerPubKeyReceived event with the handshake message received (key).
Handshake.receiveKey(e.host, e.port);

// Stop the handshake server
Handshake.stopServer()

```
  
