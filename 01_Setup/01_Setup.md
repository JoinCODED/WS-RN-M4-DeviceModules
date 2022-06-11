Fork and clone [this](https://github.com/JoinCODED/Demo-RN-M4-DeviceModules) into your development directory.

1. To use a device module, we first need to ask for permission to use it.

2. Import `Location` from `expo-location`.

```js
import * as Location from 'expo-location';
```

3. In the `handleGetWeather` function, we will first use `requestForegroundPermissionsAsync` to request permission to use the device's location.

```js
const { status } = await Location.requestForegroundPermissionsAsync();
```

Be aware that this function is asynchronous, so we need to use the `await` keyword to wait for the result.
And this will prompt the user to enable location services if they have not already done so.

If the user has enabled location services, the `status` will be `granted`.

4. We will check the `status` to see if the user has granted permission to use the device's location. and if they have not, we will throw an error.

```js
if (status !== 'granted') {
  return setError('Permission to access location was denied.');
}
```
