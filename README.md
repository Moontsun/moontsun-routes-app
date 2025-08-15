import React, { useState, useEffect } from 'react';
import { StyleSheet, View } from 'react-native';
import MapView, { Marker } from 'react-native-maps';

export default function App() {
  const [revendedoras, setRevendedoras] = useState([
    { id: 1, nome: 'Maria', latitude: -30.0346, longitude: -51.2177 },
    { id: 2, nome: 'Ana', latitude: -30.0400, longitude: -51.2200 },
  ]);

  return (
    <View style={styles.container}>
      <MapView
        style={styles.map}
        initialRegion={{
          latitude: -30.0346,
          longitude: -51.2177,
          latitudeDelta: 0.05,
          longitudeDelta: 0.05,
        }}
      >
        {revendedoras.map((r) => (
          <Marker
            key={r.id}
            coordinate={{ latitude: r.latitude, longitude: r.longitude }}
            title={r.nome}
          />
        ))}
      </MapView>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
  map: {
    width: '100%',
    height: '100%',
  },
});
