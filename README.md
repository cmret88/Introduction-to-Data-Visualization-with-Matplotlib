# Introduction-to-Data-Visualization-with-Matplotlib
# Matplotlib Data Visualization

# Introducing the pyplot interface
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
plt.show()
# figure object is a container that holds everything
# axis object holds the data, it's the canvass

# Adding data to axes
# below is a DataFrame that contains info about weather in Seattle in different months
seattle_weather['MONTH']
# monthly avg normal temp column contains temps in these month averaged over 10 year period
seattle_weather['MLY-TAVG-NORMAL']
# to add data to axes, we call a plotting command
# these are methods of axes objects
# then call the plt command
ax.plot(seattle_weather['MONTH'], seattle_weather['MLY-TAVG-NORMAL'])
plt.show()
# horizontal axis is months, height axis is temp
# you can add more data to the plot
ax.plot(austin_weather['MONTH'], austin_weather['MLY-TAVG-NORMAL'])
plt.show()

# putting it all together
fig, ax = plt.subplots()
ax.plot(seattle_weather['MONTH'], seattle_weather['MLY-TAVG-NORMAL'])
ax.plot(austin_weather['MONTH'], austin_weather['MLY-TAVG-NORMAL'])
plt.show()
