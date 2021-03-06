# enviro-monitor
This project uses a Raspberry Pi Zero W, a Pimoroni Enviro+ and a Plantower air quality sensor to monitor, display and report on air particles, gases, temperature, humidity and air pressure. It’s based on many of the Python [examples and libraries]( https://github.com/pimoroni/enviroplus-python) published by Pimoroni, with the following modifications and enhancements:

A basic weather forecast function, based on air pressure levels and changes.

The light level display in the superb [Weather and Light](https://github.com/pimoroni/enviroplus-python/blob/master/examples/weather-and-light.py) has been changed to air quality. It also uses the above-mentioned weather forecast information and has some minor changes to the humidity indicator.

The [Combined]( https://github.com/pimoroni/enviroplus-python/blob/master/examples/combined.py) has been modified to provide a more visible display of each graph, to use graph colours based on level thresholds for each parameter and to only display parameters that have been measured. The display_everything method has also been modified to only show air quality parameters, in order to improve readability of the display.

The [All in One]( https://github.com/pimoroni/enviroplus-python/blob/master/examples/all-in-one.py) function has been modified to allow cycling through the monitor’s functions.

The accuracy of the temperature and humidity measurements has been improved by undertaking extensive testing and [regression analysis](https://github.com/roscoe81/enviro-monitor/blob/master/Regression_Analysis/Northcliff_Enviro_Monitor_Regression_Analyser.py) to develop more effective compensation algorithms. However on their own, even these improved algorithms were not sufficient and it was necessary to use a [3D-printed case](https://github.com/roscoe81/enviro-monitor/tree/master/3DP_Files) to separate the Enviro+ from the Raspberry Pi Zero W and connect them together via a ribbon cable. The case needs to be sheltered from the elements and the [base](https://github.com/roscoe81/enviro-monitor/blob/master/3DP_Files/Northcliff_EM_Base_01.stl) is only required if the unit is not mounted on a vertical surface.

Likewise, testing and regression analysis was used to provide time-based drift, temperature, humidity and air pressure compensation for the Enviro+ gas sensors. Algorithms and clean-air calibration is included to provide gas sensor readings in ppm. A data logging function is provided to support the regression analysis. The log file needs to be converted to a valid json format before undertaking the regression analysis.

## Note: Even though the accuracy has been improved, the readings are still not thoroughly and accurately calibrated and should not be relied upon for critical purposes or applications.

mqtt support is provided to use external temperature and humidity sensors (for data logging and regression analysis), interworking between the monitor and a [home automation system](https://github.com/roscoe81/Home-Manager) and to support interworking between outdoor and indoor sensors. That latter interworking allows the display of an indoor unit to cycle between indoor and outdoor readings.

[Luftdaten]( https://github.com/pimoroni/enviroplus-python/blob/master/examples/luftdaten.py)  interworking is essentially unchanged, other than the ability to use external temperature and humidity sensors via mqtt messages. 

The same [Enviro+ setup]( https://github.com/pimoroni/enviroplus-python/blob/master/README.md) is used and the Config Setup parameters in the code can be further used to customise its functionality.

## License
This project is licensed under the MIT License - see the LICENSE.md file for details

## Acknowledgements
Relative Humidity Temperature adjustment using August-Roche_Magnus approximation using https://bmcnoldy.rsmas.miami.edu/Humidity.html

Weather Forecast based on www.worldstormcentral.co/law_of_storms/secret_law_of_storms.html by R. J. Ellis
