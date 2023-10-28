# Project
INF-201 Assignment_4
---------------------------------------------------------WeatherAppGui-------------------------------------------------------------------------------------
I have created a Java class called `WeatherAppGui`, which represents a basic graphical user interface (GUI) for a weather application. Let me explain what the code does:

First, I imported the necessary Java libraries, including the JSON library (`org.json.simple.JSONObject`) for handling JSON data and libraries for GUI elements (`javax.swing` and `java.awt`).

Next, I defined the `WeatherAppGui` class, which extends `JFrame`. This class is used to create the main window for the GUI.

In the constructor of the `WeatherAppGui` class, I initialized the GUI window. I set the window's title, specified that the program should exit when the window is closed, defined its size, centered it on the screen, disabled resizing, and set the layout manager to `null` so that I can manually position the components.

The `addGuiComponents` method is responsible for adding various GUI components to the window. These components include:
   - A text field for entering a location to search for weather information.
   - An image (represented by a `JLabel`) to display the weather condition icon.
   - A label for displaying the temperature.
   - A label for showing the weather condition description.
   - An image for displaying the humidity icon.
   - A label for presenting humidity information.
   - An image for displaying the windspeed icon.
   - A label for displaying windspeed information.
   - A search button (represented by an image).

I've also implemented the `loadImage` method to load and display images in the GUI. It takes a resource path as an argument, reads the image from the specified file, and returns an `ImageIcon` that can be used to display the image.

The `searchButton` is a button that, when clicked, triggers an action to retrieve weather data based on the user's input location. This data is fetched by calling a `WeatherApp.getWeatherData(userInput)` method (not shown in the provided code).

Once the weather data is retrieved, I update the GUI components with the information, including the weather image, temperature, weather condition description, humidity, and windspeed.

I also included logic to select the appropriate weather image based on the weather condition obtained from the weather data. I used a `switch` statement to choose the correct image to display.

Please note that the `WeatherAppGui` class does not provide the implementation for the `getWeatherData` method. You would need to implement this method elsewhere to actually fetch weather data based on the user's input.

In summary, I've created a simple Java GUI application that allows users to input a location, fetch weather data, and display that data on the interface, including weather condition icons, temperature, humidity, and windspeed. The weather data is retrieved and updated when the user clicks the search button, but the actual implementation of the weather data retrieval is not included in this code.

---------------------------------------------------------WeatherApp----------------------------------------------------------------------------------------
This code represents a Java program that's designed to fetch weather data from an external API, process that data, and provide it in a format that can be used for display in a graphical user interface (GUI).

I've defined a class called `WeatherApp` within a package named "Assignment_4."

I've created a static method named `getWeatherData` which takes a location name as a parameter. The primary purpose of this method is to obtain weather data for the specified location.

Within the `getWeatherData` method, I first call another method called `getLocationData` to get the geographic coordinates (latitude and longitude) for the given location name. These coordinates are essential for making a request to the weather API.

Once I have the location coordinates, I construct a URL to the weather API (in this case, it's "https://api.open-meteo.com/v1/forecast") by adding latitude, longitude, and various other parameters, including the request for hourly data and the time zone.

I then use an HTTP connection to send a request to the API by calling the `fetchApiResponse` method. This method establishes a connection, sends a GET request, and retrieves the API's response.

I check the response code, and if it's not 200 (which means the connection wasn't successful), I print an error message and return `null`.

If the connection is successful, I read the JSON response from the API and parse it using the `JSONParser` from the JSON-Simple library. The JSON data contains hourly weather information.

I find the index of the current time within the hourly data to get the weather information for the present hour.

I extract various weather-related data from the JSON response, including temperature, weather condition, humidity, and wind speed.

Finally, I create a JSON object containing this weather data and return it. This data can be used by the frontend GUI for display.

I've also included another method called `getLocationData`, which is responsible for obtaining geographic coordinates for a given location name using a geocoding API. This method processes the API response in a similar way and returns the location data.

There are several helper methods in the code, such as `fetchApiResponse` for making API requests, `findIndexOfCurrentTime` for locating the index of the current time in the hourly data, and `getCurrentTime` for obtaining the current time in a specific format.

The `convertWeatherCode` method is used to convert numerical weather codes into more readable weather conditions, such as "Clear," "Cloudy," "Rain," or "Snow."

Overall, this Java code serves as the backend logic for a weather application, responsible for retrieving weather data from an API and preparing it for display in a GUI.

---------------------------------------------------------AppLauncher---------------------------------------------------------------------------------------
I created a Java program as part of my Assignment 4 to launch a graphical user interface (GUI) application. In the `main` method of my `AppLauncher` class, I used Swing, a Java library for creating GUIs.

Within the `main` method, I ensured that GUI-related operations run on the Event Dispatch Thread (EDT) using `SwingUtilities.invokeLater()`. The EDT is a specialized thread for handling GUI updates and user interactions.

In the anonymous class's `run` method, I did the following:
- I created an instance of the `WeatherAppGui` class, which likely represents the main window of a weather application.
- I made this GUI window visible to the user by calling `setVisible(true)` on the `WeatherAppGui` instance.

So, the code prepares the GUI environment to run on the EDT and then displays the `WeatherAppGui` to the user, assuming it's a GUI for a weather application.
