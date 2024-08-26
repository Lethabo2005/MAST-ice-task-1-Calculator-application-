# MAST-ice-task-1-Calculator-application- 

Here are the codes for my calculator app ice task. 

import React, { useState } from 'react';
import { StyleSheet, Text, View, TouchableOpacity } from 'react-native';

export default function App() {
  const [display, setDisplay] = useState('');
  const [result, setResult] = useState('');

  const handlePress = (buttonValue) => {
    if (buttonValue === '=') {
      calculateResult();
    } else if (buttonValue === 'C') {
      clearDisplay();
    } else {
      setDisplay(display + buttonValue);
    }
  };

  const calculateResult = () => {
    try {
      const evalResult = eval(display);
      setResult(evalResult.toString());
    } catch (error) {
      setResult('Error');
    }
  };

  const clearDisplay = () => {
    setDisplay('');
    setResult('');
  };

  return (
    <View style={styles.container}>
      <Text style={styles.heading}>My Calculator App</Text>
      <View style={styles.resultContainer}>
        <Text style={styles.displayText}>{display}</Text>
        <Text style={styles.resultText}>{result}</Text>
      </View>
      <View style={styles.buttonsContainer}>
        {['7', '8', '9', '/', '4', '5', '6', '*', '1', '2', '3', '-', 'C', '0', '=', '+'].map((buttonValue) => (
          <TouchableOpacity
            key={buttonValue}
            style={styles.button}
            onPress={() => handlePress(buttonValue)}
          >
            <Text style={styles.buttonText}>{buttonValue}</Text>
          </TouchableOpacity>
        ))}
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    backgroundColor: '#fff',
  },
  heading: {
    fontSize: 24,
    fontWeight: 'bold', 
    textAlign: 'center',
    marginVertical: 20,
    color: '#000',
  },
  resultContainer: {
    flex: 2,
    justifyContent: 'center',
    alignItems: 'flex-end',
    padding: 10,
    backgroundColor: '#f0f0f0',
  },
  displayText: {
    fontSize: 40,
    color: '#000',
  },
  resultText: {
    fontSize: 30,
    color: '#888',
  },
  buttonsContainer: {
    flex: 5,
    flexDirection: 'row',
    flexWrap: 'wrap',
  },
  button: {
    width: '23%',
    height: '20%',
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#d4d4d2',
    borderWidth: 0.5,
    borderColor: '#888',
  },
  buttonText: {
    fontSize: 28,
    color: '#000',
  },
}); 
