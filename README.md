# Juan-Florez-Juan-Canas
import React from 'react'
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import { Provider as PaperProvider } from 'react-native-paper';
import Home from './src/component/Home';
import Catalog from './src/component/Screens/Catalog';
import Contact from './src/component/Screens/Contact';
import FindVehicle from './src/component/Screens/FindVehicle';
import DriveTesting from './src/component/Screens/DriveTesting';
import CotizationForm from './src/component/Screens/CotizationForm';
import Mechanic from './src/component/Screens/Mechanic';
import History from './src/component/Screens/History';
import Promotions from './src/component/Screens/Promotions';

 
 
const Stack = createStackNavigator();
 
const App = () => {
  return (
    <PaperProvider>
      <NavigationContainer>
        <Stack.Navigator>
          <Stack.Screen name="Home" component={Home}/>
          <Stack.Screen name="Catalog" component={Catalog}/>
          <Stack.Screen name="FindVehicle" component={FindVehicle}/>
          <Stack.Screen name="DriveTesting" component={DriveTesting}/>
          <Stack.Screen name="CotizationForm" component={CotizationForm}/>
          <Stack.Screen name="Mechanic" component={Mechanic}/>
          <Stack.Screen name="History" component={History}/>
          <Stack.Screen name="Promotions" component={Promotions}/>
          <Stack.Screen name="Contact" component={Contact}/>
        </Stack.Navigator>
      </NavigationContainer>
    </PaperProvider> 
  )
}
export default App

*******************************************************************************************************************************************************************************
import React from 'react'
import { StyleSheet, View, Text } from 'react-native'
import { Button } from 'react-native-paper'

const Home = ({ navigation }) => {
  return (
        <View style={styles.contains}>
            <Text style={styles.title}> BIENVENIDOS A CONSECIONARIOS JyJ.</Text>
            <Text style={styles.space}></Text>
            <Button mode='contained-tonal' onPress={()=>navigation.navigate("Catalog")}>Catalogo</Button>
            <Text style={styles.space}></Text>
            <Button mode='contained-tonal' onPress={()=>navigation.navigate('FindVehicle')}>Busqueda Vehiculo</Button>
            <Text style={styles.space}></Text>
            <Button mode='contained-tonal' onPress={()=>navigation.navigate('DriveTesting')}>Prueba de Manejo</Button>
            <Text style={styles.space}></Text>
            <Button mode='contained-tonal' onPress={()=>navigation.navigate('CotizacionForm')}>Cotizar vehiculo</Button>
            <Text style={styles.space}></Text>
            <Button mode='contained-tonal' onPress={()=>navigation.navigate('Mechanic')}>Taller</Button>
            <Text style={styles.space}></Text>
            <Button mode='contained-tonal' onPress={()=>navigation.navigate('History')}>Historial Servicios</Button>
            <Text style={styles.space}></Text>
            <Button mode='contained-tonal' onPress={()=>navigation.navigate("Promotions")}>Promociones</Button>
            <Text style={styles.space}></Text>
            <Button mode='contained-tonal' onPress={()=>navigation.navigate("Contact")}>Contactanos</Button>
        </View>
  )
}

const styles = StyleSheet.create({
    contains:{
        flex:1,
        backgroundColor: 'black',
        justifyContent: 'center',
    },
    space:{
        fontSize:10,
    },
    title:{
        color: 'rgb(199, 101, 101)',
        fontSize: 40,
        textAlign: 'center'
    },
    Button:{
        color: 'rgb(236, 87, 87)',
        marginVertical: 20,
        paddingHorizontal: 10,
        paddingVertical: 10,
        color: 'white',
    },
});

export default Home
*******************************************************************************************************************************************************************************
import React from 'react';
import VehicleList from './VehicleList';

const Catalog = () => {

    const vehicles = [
        {
            id: 1,
            imageUrl: 'https://loscoches.com/wp-content/uploads/2022/01/honda-civic-type-r-deportivo.jpg',
            description: 'Honda Civic',
            price: 25000
            
        },
        {
            id: 2,
            imageUrl:'https://www.latercera.com/resizer/o9pSNX27e4Habo1khwmsHtrr0Zs=/900x600/smart/arc-anglerfish-arc2-prod-copesa.s3.amazonaws.com/public/RP5XD5W7ERASLG5HD3LOVOXUQM.jpg',
            description: 'Mitsibishi Lancer',
            price: 30000,
        },
        {
            id: 3,
            imageUrl: 'https://neomotor.epe.es/binrepository/990x557/0c0/0d0/none/2594535/BNXT/imagen74_NM75_MG7770706.jpeg',
            description: 'Porsche Panamera',
            price: 40000,
        },

    ];

    return <VehicleList vehicles={vehicles}/>;

}

export default Catalog;
*******************************************************************************************************************************************************************************
import React from 'react';
import { Image, StyleSheet, Text, View } from 'react-native';

const Vehicle = ({imageUrl,description, price}) => {
  return (
    <View style={styles.container}>
        <Image
            source={{uri:imageUrl}}
            style={styles.image}
        />
        <Text style ={{marginTop: 10, color: 'white'}}>
          {description}
        </Text>
        <Text></Text>
        <Text style={{marginTop: 5, fontWeight: 'bold', color: 'white'}}>$ {price}</Text>   
    </View>
  );
};

const styles=StyleSheet.create({
  container: {
    backgroundColor: 'black',
    alignItems: 'center'
  },
    image:{ 
        width:300,
        height:200,
      }
});
export default Vehicle;
*******************************************************************************************************************************************************************************
import React from 'react';
import { ScrollView } from 'react-native';
import Vehicle from './Vehicle';

const VehicleList = ({vehicles,motorcycle}) => {
  return (
    <ScrollView>
        {vehicles.map((vehicle) => (
            <Vehicle
                key={vehicle.id}
                imageUrl={vehicle.imageUrl}
                description={vehicle.description}
                price={vehicle.price}
            />
        ))}
    </ScrollView>
  );
};

export default VehicleList;
*******************************************************************************************************************************************************************************
import React from 'react'
import { StyleSheet, View, Text} from 'react-native'

const Contact = () => {
  return (
    <View style={styles.contains}>
      <Text style={styles.title}> Esperamos tu mensaje,
      WhatsApp: 3002200000 </Text>
    </View>
  );
};

const styles = StyleSheet.create({
    contains:{
        flex:1,
        backgroundColor: 'black',
        justifyContent: 'center',
    },
    title:{
        color: 'rgb(199, 101, 101)',
        fontSize: 40,
        textAlign: 'center'
    },
});

export default Contact
*******************************************************************************************************************************************************************************
import React, { useState } from 'react';
import { View, Text, TextInput, Button, StyleSheet } from 'react-native';

const CotizacionForm = () => {
  const [fechaAgenda, setFechaAgenda] = useState('');
  const [nombre, setNombre] = useState('');
  const [apellido, setApellido] = useState('');
  const [ccPersona, setCcPersona] = useState('');
  const [carroCotizar, setCarroCotizar] = useState('');
  const [precioCarro, setPrecioCarro] = useState('');

  const handleCotizacionSubmit = () => {

    console.log({
      fechaAgenda,
      nombre,
      apellido,
      ccPersona,
      carroCotizar,
      precioCarro,
    });
  };

  return (
    <View style={styles.container}>
      <Text style={styles.label}>Fecha de Agenda:</Text>
      <TextInput
        style={styles.input}
        value={fechaAgenda}
        onChangeText={setFechaAgenda}
      />
      <Text style={styles.label}>Nombre:</Text>
      <TextInput
        style={styles.input}
        value={nombre}
        onChangeText={setNombre}
      />
      <Text style={styles.label}>Apellido:</Text>
      <TextInput
        style={styles.input}
        value={apellido}
        onChangeText={setApellido}
      />
      <Text style={styles.label}>Cédula:</Text>
      <TextInput
        style={styles.input}
        value={ccPersona}
        onChangeText={setCcPersona}
      />
      <Text style={styles.label}>Carro a cotizar:</Text>
      <TextInput
        style={styles.input}
        value={carroCotizar}
        onChangeText={setCarroCotizar}
      />
      <Text style={styles.label}>Precio del carro:</Text>
      <TextInput
        style={styles.input}
        value={precioCarro}
        onChangeText={setPrecioCarro}
        keyboardType="numeric"
      />
      <Button title="Enviar Cotización" onPress={handleCotizacionSubmit} />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    padding: 20,
  },
  label: {
    fontSize: 16,
    marginBottom: 5,
  },
  input: {
    borderWidth: 1,
    borderColor: '#ccc',
    borderRadius: 5,
    padding: 10,
    marginBottom: 10,
  },
});

export default CotizacionForm;
*******************************************************************************************************************************************************************************
import React from 'react'
import { StyleSheet, Text, View } from 'react-native'
import { useNavigation } from '@react-navigation/native';

const DriveTesting = () => {
    const navigation = useNavigation();
  return (
    <View>
        <Text>Agenda tu prueba de manejo</Text>
    </View>
  )
}

const styles = StyleSheet.create({
    contains:{
        flex:1,
        backgroundColor: 'black',
        justifyContent: 'center',
    },
    title:{
        color: 'rgb(199, 101, 101)',
        fontSize: 40,
        textAlign: 'center'
    },
});

export default DriveTesting
*******************************************************************************************************************************************************************************
import React from 'react'
import { View } from 'react-native'

const FindVehicle = () => {
    return (
        <View>
            <Text>Quieres buscar tu vehiculo soñado</Text>
        </View>
      )
    }
    
    const styles = StyleSheet.create({
        contains:{
            flex:1,
            backgroundColor: 'black',
            justifyContent: 'center',
        },
        title:{
            color: 'rgb(199, 101, 101)',
            fontSize: 40,
            textAlign: 'center'
        },
    });
export default FindVehicle
*******************************************************************************************************************************************************************************
  import React from 'react'
import { StyleSheet, View } from 'react-native'
import { Text } from 'react-native-paper'

const History = () => {
return (
    <View style={styles.contains}>
        <Text style={styles.title}>Revisa el Historial de tu vehiculo</Text>
        </View>
      );
    };
    
    const styles = StyleSheet.create({
        contains:{
            flex:1,
            backgroundColor: 'black',
            justifyContent: 'center',
        },
        title:{
            color: 'rgb(199, 101, 101)',
            fontSize: 40,
            textAlign: 'center'
        },
    });

export default History
*******************************************************************************************************************************************************************************
import React from 'react'
import { StyleSheet, View } from 'react-native'
import { Text } from 'react-native-paper';

const Mechanic = () => {
    return (
    <View style={styles.contains}>
        <Text style={styles.title}> Agenda tu cita de revicion en nuestro taller.</Text>
        <Text>1. Mecanica General</Text>
        <Text>2. Alineacion y Balanceo</Text>
        <Text>3. Mantenimiento de Frenos</Text>
    </View>
      );
    };
    
    const styles = StyleSheet.create({
        contains:{
            flex:1,
            backgroundColor: 'black',
            justifyContent: 'center',
        },
        title:{
            color: 'rgb(199, 101, 101)',
            fontSize: 40,
            textAlign: 'center'
        },
    });
export default Mechanic

*******************************************************************************************************************************************************************************
import React from 'react'
import { StyleSheet, View } from 'react-native'

const Promotions = () => {
    return (
        <View style={styles.contains}>
          <Text style={styles.title}> Muy Pronto Estaran Habilitadas Nuestras Promociones</Text>
        </View>
      );
    };
    
    const styles = StyleSheet.create({
        contains:{
            flex:1,
            backgroundColor: 'black',
            justifyContent: 'center',
        },
        title:{
            color: 'rgb(199, 101, 101)',
            fontSize: 40,
            textAlign: 'center'
        },
    });

export default Promotions

*******************************************************************************************************************************************************************************
import React, { useState } from 'react';
import { View, Text, } from 'react-native';
import globalStyles from '../styles/globalStyles';
import { PaperProvider, Button, TextInput } from 'react-native-paper';
 
const AppointmentForm = ({ navigation }) => {
  const [name, setName] = useState('');
  const [date, setDate] = useState('');
  const [time, setTime] = useState('');
 
  const handleSubmit = () => {
    // Handle form submission here
    console.log('Name:', name);
    console.log('Date:', date);
    console.log('Time:', time);
   
    navigation.navigate('Confirmation', { name: name, date: date, time: time });
  };
 
  return (
    <PaperProvider>
      <View>
        <Text style={globalStyles.label}>Name:</Text>
        <TextInput
          style={globalStyles.textInput}
          value={name}
          onChangeText={name => setName(name)} />
 
        <Text style={globalStyles.label}>Date:</Text>
        <TextInput
          style={globalStyles.textInput}
          value={date}
          onChangeText={date => setDate(date)} />
 
        <Text
          style={globalStyles.label}>Time:</Text>
        <TextInput
          style={globalStyles.textInput}
          value={time}
          onChangeText={time => setTime(time)} />
 
        <Button
          style={globalStyles.button}
          mode = 'contained'
          title="Submit" onPress={handleSubmit}>
            Enviar
        </Button>
      </View>
    </PaperProvider>
  );
};
 
export default AppointmentForm;
*******************************************************************************************************************************************************************************
