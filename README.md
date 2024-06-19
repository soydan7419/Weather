# MDS-proiect
## Weather forecasting

This program is a weather forecasting web application written in Java.

### Team members:
- [Soydan Alperen](https://github.com/soydan7419/Weather.git)
- [Shahsavari Mohammad](https://github.com/MohammadShahsavarii/MDS-proiect.git)

### Description of application:
This program is a weather forecasting web application written in Java.
Usually, people plan their trip so that they can make the best use of their time. Also, in terms of agriculture, weather forecasting is a very important issue for planting, spraying and harvesting. In other matters, even such as airline companies, tourism tours, maritime and military affairs, weather forecasting is one of the principles of planning the above matters.
In this program, we can see the weather forecast. For example, if you plan to travel to another country, you can use this app to see the weather there. The program analyzes itself every time. In other words, it recalculates the weather forecast.

### User Story: 
As a Busy Professional, I Want Hyper-Localized Weather Information at a Glance.
As a busy professional, my mornings are hectic. Before I step out, I need precise weather details for my specific neighborhood. Will it rain during my walk to work? Should I grab an umbrella or sunglasses? Scouring generic city-wide forecasts wastes valuable time.

#### Desired Functionality:
1. Geolocation Retrieval:
   - Upon visiting the web app, it automatically detects my current location using geolocation.
2. Key Weather Information:
   - Display the current temperature, "feels-like" temperature, weather conditions (sunny, rainy, cloudy), and precipitation probability for my exact area.
3. Short-Term Forecast:
   - Provide an easy-to-understand forecast for the next few hours, highlighting any weather changes.
4. User-Friendly Design:
   - Keep the interface clean and uncluttered, emphasizing relevant weather data.
5. Real-Time Updates:
   - Ensure real-time or frequent (at least every few minutes) weather updates.
6. Accessibility:
   - Make the forecast understandable even for non-weather enthusiasts.


### Backlog:
1. Geolocation Integration:
   - Implement geolocation services to automatically detect the user's location.
   - Request user permission for geolocation access.
   - Handle cases where geolocation is unavailable or denied.

2. Weather Data Retrieval:
   - Integrate with a reliable weather API to fetch hyper-localized weather data.
   - Retrieve current temperature, "feels-like" temperature, weather conditions, and precipitation probability for the user's area.

3. User Interface Design:
   - Create a clean, intuitive interface:
     - Display the key weather information prominently.
     - Use clear icons or visual cues for weather conditions.
     - Consider a minimalistic design to avoid clutter.
     - Ensure responsiveness for different devices.

4. Short-Term Forecast Display:
   - Develop a concise forecast section:
     - Show the next few hours' weather details.
     - Highlight any significant changes.
     - Use simple language.

5. Real-Time Updates:
   - Set up a background service to fetch updated weather data:
     - Regularly poll the weather API.
     - Notify users of any significant changes.

6. Accessibility Considerations:
    - Ensure the app is usable by everyone:
     - Use alt text for weather icons.
     - Provide high contrast and legible fonts.
     - Test with users who are not weather enthusiasts to validate clarity.


### UML diagram
UML diagram of the model
![overall-architecture](https://github.com/MohammadShahsavarii/MDS-proiect/assets/127997195/3770ce14-8572-4751-9879-d75079f1239e)

### How does the application works?
Application receives the requested via /v1/api/open-weather/{city} url with {city} path variables
There is a validation for city parameter. City value can not be decimal or a blank value.
If the city value is not valid, api returns 400 - Http Bad Request response
Current weather report can be fetch either from database or WeatherStackAPI with the API_KEY
If the latest data is not older than 30 minutes for that city value, data is fetching from db.
Either city does not exist or older than 30 minutes in DB, a request sends to WeatherStackAPI and the result puts to Cache
If there is a value with city filter as key in cache, the response is returns from cache directly
On the swagger page you can find the relevant api endpoint. You can reach the openapi page by http://localhost:8080/swagger-ui/index.html url.

You can define WEATHER_STACK_API_KEY in the .env file

### How Does the System Work?
The user enters the name of the city for which he wants to know the weather.
The open-weather-service-app-1 app sends the city name to the CityNameValidator app.
The CityNameValidator application checks whether the city name is valid.
If the city name is valid, the open-weather-service-app-1 app retrieves the weather data by communicating with the Open Weather API.
If the weather data is not retrieved from the cache, the open-weather-service-app-1 application sends the weather data to the Weatherstuck API application.
The Weatherstuck API implementation caches weather data.
The Weatherstuck API application sends weather data to the WeatherRepository application.
The WeatherRepository application stores weather data in the WeatherDB database.
The open-weather-service-app-1 application displays weather data to the user.

#### System Features:
Modular: The system consists of modules that can operate independently of each other.
Cached: Weather data is cached, reducing the number of calls to the Open Weather API.
Fault Tolerant: The system is protected against errors.
Scalable: The system can be easily scaled to support more users.
User-Friendly: The system is easy to use.

#### Advantages of the System:
Fast: The system provides weather data quickly.
Reliable: The system is error-proof.
Scalable: The system can be easily scaled to support more users.
User-Friendly: The system is easy to use.

#### Disadvantages of the System:
Complex: The system is complex.
Expensive: The system is expensive.
Dependent: The system depends on the Open Weather API.
Future Development of the System:
The system can be enhanced to provide weather data in real time.
The system can be enhanced to visualize weather data.
The system can be improved to predict weather data.

#### Areas of Use of the System:
weather apps
weather forecasts
weather alerts
Agriculture
Aviation
Tourism

#### Technologies:
Java 17, Spring Boot 3.0, Open API Documentation, Spring Data JPA, Kotlin, H2 In Memory Database, Restful API, Maven, Junit5, Mockito, Integration Tests, Docker, Docker Compose, Github Actions, Prometheus, Grafana, Prerequisites, Maven or Docker, Docker Run
The application can be built and run by the Docker engine. The Dockerfile has multistage build, so you do not need to build and run separately.
Please follow the below directions in order to build and run the application with Docker Compose;

$ cd open-weather $ docker-compose up -d Docker compose creates 3 replicas (instances) of the application on port range 9595-9597

You can reach the open-api-ui via http://{HOST}:{9595-9597}/swagger-ui.html Prometheus You can reach prometheus page via http://{HOST}:9090

Grafana You can reach grafana page via http://{HOST}:3000 - GF_SECURITY_ADMIN_PASSWORD=admin

Maven Run To build and run the application with Maven, please follow the directions below;

$ cd open-weather $ mvn clean install $ mvn spring-boot:run You can reach the swagger-ui via http://{HOST}:8080/swagger-ui.html

### YouTube
- [Demo1](https://youtu.be/4bHROoWFPSk?si=RuGcY2ylAPi9pEnt)
- [Demo2](https://youtu.be/MRxxE1A2Ads?si=CDa6A-QXtmN-IcFG)