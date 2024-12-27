# Code 1
import React, { useState } from 'react';
import { StyleSheet, View } from 'react-native';
import Display from './components/Display';
import Button from './components/Button';

const App = () => {
  const [expression, setExpression] = useState('');
  const [result, setResult] = useState('');

  const handlePress = (value) => {
    if (value === '=') {
      try {
        setResult(eval(expression).toString());
      } catch (error) {
        setResult('Error');
      }
    } else if (value === 'C') {
      setExpression('');
      setResult('');
    } else {
      setExpression((prev) => prev + value);
    }
  };

  return (
    <View style={styles.container}>
      <Display expression={expression} result={result} />
      <View style={styles.buttonContainer}>
        {['7', '8', '9', '/', '4', '5', '6', '*', '1', '2', '3', '-', 'C', '0', '=', '+'].map((btn) => (
          <Button key={btn} value={btn} onPress={handlePress} />
        ))}
      </View>
    </View>
  );
};

const styles = StyleSheet.create({
  container: { flex: 1, justifyContent: 'center', backgroundColor: '#f5f5f5' },
  buttonContainer: { flexDirection: 'row', flexWrap: 'wrap', justifyContent: 'center' },
});

export default App;

# code 2

import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

const Display = ({ expression, result }) => (
  <View style={styles.display}>
    <Text style={styles.expression}>{expression}</Text>
    <Text style={styles.result}>{result}</Text>
  </View>
);

const styles = StyleSheet.create({
  display: {
    height: 150,
    justifyContent: 'center',
    alignItems: 'flex-end',
    paddingHorizontal: 20,
    backgroundColor: '#e6e6e6',
    marginBottom: 20,
  },
  expression: { fontSize: 24, color: '#333' },
  result: { fontSize: 40, fontWeight: 'bold', color: '#000' },
});
export default Display;

# code 3
import React from 'react';
import { TouchableOpacity, Text, StyleSheet } from 'react-native';

const Button = ({ value, onPress }) => (
  <TouchableOpacity style={styles.button} onPress={() => onPress(value)}>
    <Text style={styles.text}>{value}</Text>
  </TouchableOpacity>
);

const styles = StyleSheet.create({
  button: {
    width: 80,
    height: 80,
    margin: 5,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#007bff',
    borderRadius: 10,
  },
  text: { fontSize: 24, color: '#fff', fontWeight: 'bold' },
});

export default Button;

