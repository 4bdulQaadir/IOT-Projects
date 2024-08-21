#include "DHT.h"
#define DHTPIN 2 // Digital pin 2

// Define the type of DHT sensor
#define DHTTYPE DHT11 // Change to DHT22 if you're using a DHT22 sensor

// Initialize DHT sensor
DHT dht(DHTPIN, DHTTYPE);

void setup() {
  // Start serial communication for debugging purposes
  Serial.begin(9600);
  
  // Initialize the DHT sensor
  dht.begin();
}

void loop() {
  // Wait a few seconds between measurements
  delay(2000);
  
  // Read temperature as Celsius (default)
  float tempC = dht.readTemperature();
  
  // Read temperature as Fahrenheit (isFahrenheit = true)
  float tempF = dht.readTemperature(true);
  
  // Read humidity
  float humidity = dht.readHumidity();
  
  // Check if any readings failed and exit early (to try again)
  if (isnan(tempC) || isnan(tempF) || isnan(humidity)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }
  
  // Compute heat index in Fahrenheit (the default)
  float heatIndexF = dht.computeHeatIndex(tempF, humidity);
  
  // Compute heat index in Celsius
  float heatIndexC = dht.computeHeatIndex(tempC, humidity, false);
  
  // Print the results
  Serial.print("Humidity: ");
  Serial.print(humidity);
  Serial.print(" %\t");
  Serial.print("Temperature: ");
  Serial.print(tempC);
  Serial.print(" °C ");
  Serial.print(tempF);
  Serial.print(" °F\t");
  Serial.print("Heat index: ");
  Serial.print(heatIndexC);
  Serial.print(" °C ");
  Serial.print(heatIndexF);
  Serial.println(" °F");
}
