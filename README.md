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

# Import the matplotlib.pyplot submodule and name it plt
import matplotlib.pyplot as plt

# Create a Figure and an Axes with plt.subplots
fig, ax = plt.subplots()

# Plot MLY-PRCP-NORMAL from seattle_weather against the MONTH
ax.plot(seattle_weather["MONTH"], seattle_weather['MLY-PRCP-NORMAL'])

# Plot MLY-PRCP-NORMAL from austin_weather against MONTH
ax.plot(austin_weather['MONTH'], austin_weather['MLY-PRCP-NORMAL'])

# Call the show function
plt.show()

#### Customizing Your Plots ####
# Customize data appearance
# adding markers to the plot to show where the data exists
# passing lower case 'o' indicates circle markers
# passing lower case 'v' indicates upside down triangle markers
ax.plot(seattle_weather['MONTH'],
        seattle_weather['MLY-PRCP-NORMAL'],
        marker = 'o')
plt.show()

# Setting the linestyle
# makes the connecting line like a dotted line
ax.plot(seattle_weather['MONTH'],
        seattle_weather['MLY-PRCP-NORMAL'],
        marker = 'v', linestyle = '--')
plt.show()
# passing the string none (linestyle = 'None'), removes the connecting line

# Choosing color
# adding the color argument
# 'r' means a red line
fig, ax = plt.subplots()
ax.plot(seattle_weather['MONTH'],
        seattle_weather['MLY-PRCP-NORMAL'],
        marker = 'v', linestyle = '--', color = 'r')
plt.show()

# Customizing the axes labels
# axis labels are capitalized
ax.set_xlabel('Time (months)')
plt.show()

ax.set_xlabel('Time (months)')
ax.set_ylabel('Average temperature (Farenheit degrees)')
plt.show()

# Adding a title
ax.set_title('Weather in Seattle')
plt.show()

# Plot Seattle data, setting data appearance
ax.plot(seattle_weather["MONTH"], 
        seattle_weather["MLY-PRCP-NORMAL"], 
        marker = 'o', linestyle = '--', color = 'b')

# Plot Austin data, setting data appearance
ax.plot(austin_weather["MONTH"], 
        austin_weather["MLY-PRCP-NORMAL"], 
        marker = 'v', linestyle = '--',color = 'r')

# Call show to display the resulting plot
plt.show()

ax.plot(seattle_weather["MONTH"], seattle_weather["MLY-PRCP-NORMAL"])
ax.plot(austin_weather["MONTH"], austin_weather["MLY-PRCP-NORMAL"])

# Customize the x-axis label
ax.set_xlabel('Time (months)')

# Customize the y-axis label
ax.set_ylabel('Precipitation (inches)')

# Add the title
ax.set_title('Weather patterns in Austin and Seattle')

# Display the figure
plt.show()

#### Small Multiples ###
# in some cases, adding too much data can make it too busy
# to overcome this, we can use small multiples
# also called subplots

# Small multiples with plt.subplots
fig, ax = plt.subplots()
fig, ax = plt.subplots(3, 2) # 3 rows and 2 columns
plt.show()
# to add data, we would have to index into this object and call the plot method on an element of the array
ax.shape # (3,2)
ax[0, 0].plot(seattle_weather['MONTH'],
              seattle_weather['MLY-PRCP-NORMAL'],
              color = 'b')
plt.show()

# Subplots with data
fig, ax = plt.subplots(2, 1)
ax[0].plot(seattle_weather['MONTH'], seattle_weather['MLY-PRCP-NORMAL'],
           color = 'b')
ax[0].plot(seattle_weather['MONTH'], seattle_weather['MLY-PRCP-25PCTL'],
           linestyle = '--', color = 'b')
ax[0].plot(seattle_weather['MONTH'], seattle_weather['MLY-PRCP-75PCTL'],
           linestyle = '--', color = 'b')
ax[1].plot(austin_weather['MONTH'], austin_weather['MLY-PRCP-NORMAL'],
           color = 'r')
ax[1].plot(austin_weather['MONTH'], austin_weather['MLY-PRCP-25PCTL'],
           linestyle = '--', color = 'r')
ax[1].plot(austin_weather['MONTH'], austin_weather['MLY-PRCP-75PCTL'],
           linestyle = '--', color = 'r')
ax[0].set_ylabel('Precipitation (inches)')
ax[1].set_ylabel('Precipitation (inches)')
ax[1].set_xlabel('Time (months)')
plt.show()

# sharing the y-axis range
fig, ax = plt.subplots(2, 1, sharey=True)

# Create a Figure and an array of subplots with 2 rows and 2 columns
fig, ax = plt.subplots(2, 2)

# Addressing the top left Axes as index 0, 0, plot month and Seattle precipitation
ax[0, 0].plot(seattle_weather['MONTH'], seattle_weather['MLY-PRCP-NORMAL'])

# In the top right (index 0,1), plot month and Seattle temperatures
ax[0, 1].plot(seattle_weather['MONTH'], seattle_weather['MLY-TAVG-NORMAL'])

# In the bottom left (1, 0) plot month and Austin precipitations
ax[1, 0].plot(austin_weather['MONTH'], austin_weather['MLY-PRCP-NORMAL'])

# In the bottom right (1, 1) plot month and Austin temperatures
ax[1, 1].plot(austin_weather['MONTH'], austin_weather['MLY-TAVG-NORMAL'])
plt.show()

# Create a figure and an array of axes: 2 rows, 1 column with shared y axis
fig, ax = plt.subplots(2, 1, sharey=True)

# Plot Seattle precipitation data in the top axes
ax[0].plot(seattle_weather['MONTH'], seattle_weather['MLY-PRCP-NORMAL'], color = 'b')
ax[0].plot(seattle_weather['MONTH'], seattle_weather['MLY-PRCP-25PCTL'], color = 'b', linestyle = '--')
ax[0].plot(seattle_weather['MONTH'], seattle_weather['MLY-PRCP-75PCTL'], color = 'b', linestyle = '--')

# Plot Austin precipitation data in the bottom axes
ax[1].plot(austin_weather['MONTH'], austin_weather['MLY-PRCP-NORMAL'], color = 'r')
ax[1].plot(austin_weather['MONTH'], austin_weather['MLY-PRCP-25PCTL'], color = 'r', linestyle = '--')
ax[1].plot(austin_weather['MONTH'], austin_weather['MLY-PRCP-75PCTL'], color = 'r', linestyle = '--')
plt.show()

#### Plotting time-series data ####
# many kinds of data are ordered in time-series
# we use pandas to recognize data as a time series
climate_change.index
# has datetime data type; Matplotlib recognize this as a variable that represents time
# the other two columns in this example are stored as regular columns of the DataFrame with a floating point data-type
# this will allow us to calculate them as continuous variables
# few points are NaN, or are missing

# Plotting time-series data
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.plot(climate_change.index, climate_change['co2'])
ax.set_xlabel('Time')
ax.set_ylabel('CO2 (ppm)')
plt.show()

# Zooming in on a decade
# we are slicing the period we are interested in
sixties = climate_change['1960-01-01':'1969-12-31']

fix, ax = plt.subplots()
ax.plot(sixties.index, sixties['co2'])
ax.set_xlabel('Time')
ax.set_ylabel('CO2 (ppm)')
plt.show()

# Zooming in on one year
sixty_nine = climate_change['1969-01-01':'1969-12-31']
fig, ax = plt.subplots()
ax.plot(sixty_nine.index, sixty_nine['co@'])
ax.set_xlabel('Time')
ax.set_ylabel('CO2 (ppm)')
plt.show()

# Import pandas as pd
import pandas as pd

# Read the data from file using read_csv
climate_change = pd.read_csv('climate_change.csv', parse_dates = ['date'], index_col = 'date')

import matplotlib.pyplot as plt
fig, ax = plt.subplots()

# Add the time-series for "relative_temp" to the plot
ax.plot(climate_change.index, climate_change['relative_temp'])

# Set the x-axis label
ax.set_xlabel('Time')

# Set the y-axis label
ax.set_ylabel('Relative temperature (Celsius)')

# Show the figure
plt.show()

import matplotlib.pyplot as plt

# Use plt.subplots to create fig and ax
fig, ax = plt.subplots()

# Create variable seventies with data from "1970-01-01" to "1979-12-31"
seventies = climate_change['1970-01-01':'1979-12-31']

# Add the time-series for "co2" data from seventies to the plot
ax.plot(seventies.index, seventies["co2"])

# Show the figure
plt.show()

#### Plotting time-series with different variables ####
# to relate two time-series that coincide in terms of their times, but record the values of different variables, we might want to plot them on the same axis

# plotting two time-series together
import pandas as pd
climate_change = pd.read_csv('climate_change.csv',
                              parse_dates=['date'],
                              index_col = 'date')

# as before, we can create a figure and axes and add the data from one variable to the plot
# we can add the data from the other variable to the plot
import maplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.plot(climate_change.index, climate_change['co2'])
ax.plot(climate_change.index, climate_change['relative_temp'])
ax.set_xlabel('Time')
ax.set_ylabel('CO2 (ppm)/ Relative temperature')
plt.show()

# using twin axies to align scales
fig, ax = plt.subplots()
ax.plot(climate_change.index, climate_change['co2'])
ax.set_xlabel('Time')
ax.set_ylabel('C02 (ppm)')
ax2 = ax.twinx() # the two axes share the same x-axis, but the y-axes are separate
ax2.plot(climate_change.index, climate_change['relative_temp])
ax2.set_ylabel('Relative temperature (Celsius)')
plt.show()

# separating variables by color
fig, ax = plt.subplots()
ax.plot(climate_change.index, climate_change['co2'], color = 'blue')
ax.set_xlabel('Time')
ax.set_ylabel('C02 (ppm)', color = 'blue')
ax2 = ax.twinx()
ax2.plot(climate_change.index, climate_change['relative_temp'], color = 'red')
ax2.set_ylabel('Relative temperature (Celsius)', color = 'red')
plt.show()

# coloring the ticks
fig, ax = plt.subplots()
ax.plot(climate_change.index, 
        climate_change['co2'], 
        color = 'blue')
ax.set_xlabel('Time')
ax.set_ylabel('C02 (ppm)', color = 'blue')
ax.tick_params('y', colors = 'blue')
ax2 = ax.twinx()
ax2.plot(climate_change.index, 
         climate_change['relative_temp'], 
         color = 'red')
ax2.tick_params('y', colors = 'red')
ax2.set_ylabel('Relative temperature (Celsius)', 
                color = 'red')
plt.show()

# a function that plots time-series
def plot_timeseries(axes, x,y, color, xlabel, ylabel):
  axes.plot(x,y,color=color)
  axes.set_xlabel(xlabel)
  axes.set_ylabel(ylabel, color = color)
  axes.tick_params('y', colors = color)

# using our function
fix, ax = plt.subplots()
plot_timeseries(ax, climate_change.index, climate_change['co2'],
                'blue','Time','C02 (ppm)')
ax2 = ax.twinx()
plot_timeseries(ax2, climate_change.index, 
                climate_change['relative_temp'],
                'red','Time','Relative temperature (Celsius)')
plt.show()

# Exercise
import matplotlib.pyplot as plt

# Initalize a Figure and Axes
fig, ax = plt.subplots()

# Plot the CO2 variable in blue
ax.plot(climate_change.index, climate_change['co2'], color='blue')

# Create a twin Axes that shares the x-axis
ax2 = ax.twinx()

# Plot the relative temperature in red
ax2.plot(climate_change.index, climate_change['relative_temp'], color='red')

plt.show()

# Define a function called plot_timeseries
def plot_timeseries(axes, x, y, color, xlabel, ylabel):

  # Plot the inputs x,y in the provided color
  axes.plot(x, y, color=color)

  # Set the x-axis label
  axes.set_xlabel(xlabel)

  # Set the y-axis label
  axes.set_ylabel(ylabel, color=color)

  # Set the colors tick params for y-axis
  axes.tick_params('y', colors=color)

fig, ax = plt.subplots()

# Plot the CO2 levels time-series in blue
plot_timeseries(ax, climate_change.index, climate_change['co2'], 'blue', 'Time (years)', 'CO2 levels')

# Create a twin Axes object that shares the x-axis
ax2 = ax.twinx()

# Plot the relative temperature data in red
plot_timeseries(ax, climate_change.index, climate_change['relative_temp'], 'red', 'Time (years)', 'Relative temperature (Celsius)')

plt.show()

#### Annotating time-series data ####
# Annotations are small pieces of text that refer to a particular part of the visualization
fig, ax = plt.subplots()
plot_timeseries(ax, climate_change.index, climate_change['co2'], 'blue', 'Time', 'CO2 (ppm)')
ax2 = ax.twinx()
plot_timeseries(ax2, climate_change.index, climate_change['relative_temp'], 'red', 'Time', 'Relative temperature (Celsius)')
ax2.annotate('>1 degree', xy=(pd.Timestamp('2015-10-06'), 1))

# Positioning the text
ax2.annotate('>1 degree',
             xy=(pd.Timestamp('2015-10-06'), 1),
             xytext=(pd.Timestamp('2008-10-06'), -0.2))

# Adding arrows to annotation
ax2.annotate('>1 degree',
             xy=(pd.Timestamp('2015-10-06'), 1),
             yxtext=(pd.Timestamp
             
