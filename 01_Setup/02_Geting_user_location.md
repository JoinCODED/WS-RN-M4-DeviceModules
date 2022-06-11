1. After we have got the user permission to use the device's location, we will use `getCurrentPositionAsync` to get the user's current location.

```js
const {
  coords: { latitude, longitude },
} = await Location.getCurrentPositionAsync({ accuracy: 5 });
```

2. After we got the longitude and latitude, we will use `reverseGeocodeAsync` to get the user's current address.

```js
const location = await Location.reverseGeocodeAsync(
  { latitude, longitude },
  { useGoogleMaps: false }
);
```
