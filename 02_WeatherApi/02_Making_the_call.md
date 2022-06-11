1. Let's use axios to make the API call.

```js
const response = await axios.get(
  `https://api.openweathermap.org/data/2.5/onecall?lat=${latitude}&lon=${longitude}&exclude=alerts&appid=${API_KEY}&units=metric`
);
```

2. Set the location state.

```js
setLocation(location[0]);
```

3. And lastly, the response data will return an array of daily weather data.

```js
setDaily(response.data.daily);
```

4. Our final result will be:

```js
const handleGetWeather = async () => {
  const { status } = await Location.requestForegroundPermissionsAsync();
  if (status !== 'granted') {
    return setError('Permission to access location was denied.');
  } else {
    const {
      coords: { latitude, longitude },
    } = await Location.getCurrentPositionAsync({ accuracy: 5 });
    const location = await Location.reverseGeocodeAsync(
      { latitude, longitude },
      { useGoogleMaps: false }
    );
    const response = await axios.get(
      `https://api.openweathermap.org/data/2.5/onecall?lat=${latitude}&lon=${longitude}&exclude=alerts&appid=${API_KEY}&units=metric`
    );
    setLocation(location[0]);
    setDaily(response.data.daily);
  }
};
```

5. You can find the final result [here](https://github.com/JoinCODED/Demo-RN-M4-DeviceModules/tree/solution).
