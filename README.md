This app helps chefs make menus whether it is by Appetizers, Main Courses or Desserts.

import React, { useState } from 'react';
import { StyleSheet, Text, View, TextInput, Button, ScrollView, Image } from 'react-native';
import { Picker } from '@react-native-picker/picker';

export default function DishForm() {
  const [name, setName] = useState('');
  const [description, setDescription] = useState('');
  const [course, setCourse] = useState('Appetizer');
  const [price, setPrice] = useState('');

  const handleSubmit = () => {
    console.log({ name, description, course, price });
    setName('');
    setDescription('');
    setCourse('Appetizer');
    setPrice('');
  };

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.title}>Add New Meal</Text>

      <Image
        source={{ uri: 'https://www.istockphoto.com/vector/creative-chef-hat-symbol-text-font-letter-vector-design-illustration-gm1156391956-315138639.jpg' }}
        style={styles.image}
      />

      <TextInput
        style={styles.input}
        placeholder="Name"
        value={name}
        onChangeText={setName}
      />

      <TextInput
        style={styles.input}
        placeholder="Description"
        value={description}
        onChangeText={setDescription}
        multiline
      />

      <Text style={styles.label}>Course:</Text>
      <Picker
        selectedValue={course}
        style={styles.picker}
        onValueChange={(itemValue) => setCourse(itemValue)}
      >
        <Picker.Item label="Appetizer" value="Appetizer" />
        <Picker.Item label="Main Course" value="Main Course" />
        <Picker.Item label="Dessert" value="Dessert" />
      </Picker>

      <TextInput
        style={styles.input}
        placeholder="Price"
        value={price}
        onChangeText={setPrice}
        keyboardType="numeric"
      />

      <Button title="Submit" onPress={handleSubmit} />

      <View style={styles.output}>
        <Text style={styles.outputTitle}>Entered meal</Text>
        <Text>Name: {name}</Text>
        <Text>Description: {description}</Text>
        <Text>Course: {course}</Text>
        <Text>Price: {price}</Text>
      </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    padding: 21,
    backgroundColor: '#fff',
  },
  title: {
    fontSize: 26,
    fontWeight: 'bold',
    marginBottom: 21,
  },
  image: {
    width: '100%',
    height: 220,
    marginBottom: 22,
    resizeMode: 'cover',
  },
  input: {
    borderWidth: 1,
    borderColor: 'beige',
    borderRadius: 6,
    padding: 12,
    marginBottom: 15,
  },
  picker: {
    height: 50,
    width: '100%',
    marginBottom: 17,
  },
  label: {
    fontSize: 16,
    marginBottom: 6,
  },
  output: {
    marginTop: 20,
    padding: 12,
    borderWidth: 2,
    borderColor: 'beige',
    borderRadius: 5,
  },
  outputTitle: {
    fontWeight: 'bold',
  },
});

