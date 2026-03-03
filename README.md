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
             yxtext=(pd.Timestamp('2008-10-06'), -0.2),
             arrowprops={})
             
# Customizing arrow properties
# we can also customize the appearance of the arrow
ax2.annotate('>1 degree',
             xy=(pd.Timestamp('2015-10-06'), 1),
             xytext=(pd.Timestamp('2008-10-06'), -0.2),
             arrowprops={'arrowstyle':'->','color':'gray'})

fig, ax = plt.subplots()

# Plot the relative temperature data
ax.plot(climate_change.index, climate_change['relative_temp'])

# Annotate the date at which temperatures exceeded 1 degree
ax.annotate('>1 degree',
            xy=(pd.Timestamp('2015-10-06'), 1))

plt.show()

fig, ax = plt.subplots()

# Plot the CO2 levels time-series in blue
plot_timeseries(ax, climate_change.index, climate_change['co2'], 'blue', 'Time (years)', 'CO2 levels')

# Create an Axes object that shares the x-axis
ax2 = ax.twinx()

# Plot the relative temperature data in red
plot_timeseries(ax, climate_change.index, climate_change['relative_temp'], 'red', 'Time (years)', 'Relative temp (Celsius)')

# Annotate point with relative temperature >1 degree
ax2.annotate('>1 degree', 
              xy=(pd.Timestamp('2015-10-06'), 1),
              xytext=(pd.Timestamp('2008-10-06'), -0.2),
              arrowprops={'arrowstyle':'->','color':'gray'})

plt.show()

#### Quantitative comparisons: bar charts ####
medals = pd.read_csv('medals_by_country_2016.csv', index_col=0)
fig, ax = plt.subplots()
ax.bar(medals.index, medals['Gold'])
plt.show()
# this chart shows a bar for ever row in the "Gold" column of the DataFrame where the height of the bar reps the # of that row
# the label of the x axis ticks correspond to the index of the DataFrame, contains names of different countries in the data table
# these names are long, so they overlap
# how to fix

# Interlude: rotate the tick labels
fig, ax = plt.subplots()
ax.bar(medals.index, medals["Gold"])
ax.set_xticklabels(medals.index, rotation=90)
ax.set_ylabel("Number of medals")

# Visualizing other medals
fig, ax = plt.subplots
ax.bar(medals.index, medals['Gold'])
ax.bar(medals.index, medals['Silver'], bottom = medals['Gold'])
ax.bar(medals.index, medals['Bronze']),
        bottom = medals['Gold'] + medals['Silver'])
ax.set_xticklabels(medals.index, rotation=90)
ax.set_ylabel('Number of medals')
plt.show()

# Add bars for "Gold" with the label "Gold"
ax.bar(medals.index, medals['Gold'], label='Gold')

# Stack bars for "Silver" on top with label "Silver"
ax.bar(medals.index, medals['Silver'], bottom=medals['Gold'], label='Silver')

# Stack bars for "Bronze" on top of that with label "Bronze"
ax.bar(medals.index, medals['Bronze'], label='Bronze',
       bottom=medals['Silver'] + medals['Gold'])

# Display the legend
ax.legend()

plt.show()

#### Quantitative Comparisons: Histograms ####

# a bar chart
fig, ax = plt.subplots()
ax.bar('Rowing', mens_rowing['Height'].mean())
ax.bar('Gymnastics', mens_gymnastics['Height'].mean())
ax.set_ylabel('Height (cm)')
plt.show()

# a histogram would have shown a full distribution within each variable
fig, ax = plt.subplots()
ax.hist(mens_rowing['Height'])
ax.hist(mens_gymnastics['Height'])
ax.set_xlabel('Height (cm)')
ax.set_ylabel('# of observations')
plt.show()

# labels are needed
fig, ax = plt.subplots()
ax.hist(mens_rowing['Height'], label = 'Rowing')
ax.hist(mens_gymnastics['Height'], label = 'Gymnastics')
ax.set_xlabel('Height (cm)')
ax.set_ylabel('# of observations')
ax.legend()
plt.show()

# customizing histograms: setting the # of bins
fig, ax = plt.subplots()
ax.hist(mens_rowing['Height'], label = 'Rowing', bins = 5)
ax.hist(mens_gymnastics['Height'], label = 'Gymnastics', bins = 5)
ax.set_xlabel('Height (cm)')
ax.set_ylabel('# of observations')
ax.legend()
plt.show()

# customizing histograms: setting bin boundaries
ax.hist(mens_rowing['Height'], label = 'Rowing', 
        bins = [150, 160, 170, 180, 190, 200, 210])
ax.hist(mens_gymnastics['Height'], label = 'Gymnastics', 
        bins = [150, 160, 170, 180, 190, 200, 210])
ax.set_xlabel('Height (cm)')
ax.set_ylabel('# of observations')
ax.legend()
plt.show()

# customizing histograms: transparency
ax.hist(mens_rowing['Height'], label = 'Rowing', 
        bins = [150, 160, 170, 180, 190, 200, 210]
        histtype = 'step')
ax.hist(mens_gymnastics['Height'], label = 'Gymnastics', 
        bins = [150, 160, 170, 180, 190, 200, 210],
        histtype = 'step')
ax.set_xlabel('Height (cm)')
ax.set_ylabel('# of observations')
ax.legend()
plt.show()

fig, ax = plt.subplots()
# Plot a histogram of "Weight" for mens_rowing
ax.hist(mens_rowing['Weight'])

# Compare to histogram of "Weight" for mens_gymnastics
ax.hist(mens_gymnastics['Weight'])

# Set the x-axis label to "Weight (kg)"
ax.set_xlabel('Weight (kg)')

# Set the y-axis label to "# of observations"
ax.set_ylabel('# of observations')

plt.show()

fig, ax = plt.subplots()

# Plot a histogram of "Weight" for mens_rowing
ax.hist(mens_rowing['Weight'],label = 'Rowing',
        bins = 5,
        histtype = 'step')

# Compare to histogram of "Weight" for mens_gymnastics
ax.hist(mens_gymnastics['Weight'],label = 'Gymnastics',
        bins = 5,
        histtype = 'step')

ax.set_xlabel("Weight (kg)")
ax.set_ylabel("# of observations")

# Add the legend and show the Figure
ax.legend()
plt.show()

#### Statistical Plotting ####
# this is a set of methods of using visualization to make comparisons
# adding error bars to bar charts
# error bars instead summarize the distribution of the data in one number, like the STD
# Example - Heights of medalists
fig, ax = plt.subplots()
ax.bar('Rowing',
        mens_rowing['Height'].mean(),
        yerr=mens_rowing['Height'].std())
ax.bar('Gymnastics',
        mens_gymnastics['Height'].mean(),
        yerr=mens_gymnastics['Height'].std())
ax.set_ylabel('Height'(cm)')
plt.show()

# Adding error bars to plots
fig, ax = plt.subplots()
ax.errorbar(seattle_weather['MONTH'],
            seattle_weather['MLY-TAVG-NORMAL'],
            yerr = seattle_weather['MLY-TAVG-STDDEV'])
ax.errorbar(austin_weather['MONTH'],
            austin_weather['MLY-TAVG-NORMAL'],
            yerr = austin_weather['MLY-TAVG-STDDEV'])
ax.set_ylabel('Temperature (Fahrenheit)')
plt.show()

# adding boxplots
fig, ax = plt.subplots()
ax.boxplot([mens_rowing['Height'],
            mens_gymnastics['Height']])
ax.set_xticklabels(['Rowing','Gymnastics'])
ax.set_ylabel('Height(cm)')
plt.show()

fig, ax = plt.subplots()

# Add a bar for the rowing "Height" column mean/std
ax.bar("Rowing", mens_rowing['Height'].mean(), yerr=mens_rowing['Height'].std())

# Add a bar for the gymnastics "Height" column mean/std
ax.bar('Gymnastics', mens_gymnastics['Height'].mean(), yerr=mens_gymnastics['Height'].std())

# Label the y-axis
ax.set_ylabel('Height (cm)')

plt.show()

fig, ax = plt.subplots()

fig, ax = plt.subplots()

# Add a boxplot for the "Height" column in the DataFrames
ax.boxplot([mens_rowing['Height'],
            mens_gymnastics['Height']])

# Add x-axis tick labels:
ax.set_xticklabels(['Rowing','Gymnastics'])

# Add a y-axis label
ax.set_ylabel('Height (cm)')

plt.show()

# Add Seattle temperature data in each month with error bars
ax.errorbar(seattle_weather['MONTH'], 
            seattle_weather['MLY-TAVG-NORMAL'], 
            yerr=seattle_weather['MLY-TAVG-STDDEV'])

# Add Austin temperature data in each month with error bars
ax.errorbar(austin_weather['MONTH'], 
            austin_weather['MLY-TAVG-NORMAL'], 
            yerr=austin_weather['MLY-TAVG-STDDEV'])

# Set the y-axis label
ax.set_ylabel('Temperature (Fahrenheit)')

plt.show()

#### Quantitative comparisons: scatter plots ####
# bar charts show us the values of one variable across different conditions, such as different countries
# what is you want to compare the values of different variables across observations?
# this is sometimes called a bi-variate comparison, because it involves the values of two different variables

# Introducing scatter plots
fig, ax = plt.subplots()
ax.scatter(climate_change['Co2'], climate_change['relative_temp'])
ax.set_xlabel('CO2 (ppm)')
ax.set_ylabel('Relative temperature (Celsius)')
plt.show()

# Customizing scatter plots
eighties = climate_change['1980-01-01':'1989-12-31']
nineties = climate_change['1990-01-01':'1999-12-31']
fig, ax = plt.subplots()
ax.scatter(eighties['co2'], eighties['relative_temp'],
           color='red', label='eighties')
ax.scatter(nineties['co2'], nineties['relative_temp'],
           color='blue', label='nineties')
ax.legend()

ax.set_xlabel('CO2 (ppm)')
ax.set_ylabel('Relative temperature (Celsius)')
plt.show()

# Encoding a third variable by color
# if we enter the index as input to the c key-word argument, this variable will get encoded as color
# note that this is not the color key-word argument that we used before, but instead is just the letter c
fig, ax = plt.subplots()
ax.scatter(climate_change['Co2'], climate_change['relative_temp'],
           c=climate_change.index)
ax.set_xlabel('CO2 (ppm)')
ax.set_ylabel('Relative temperature (Celsius)')
plt.show()

fig, ax = plt.subplots()

# Add data: "co2" on x-axis, "relative_temp" on y-axis
ax.scatter(climate_change['co2'], climate_change['relative_temp'])

# Set the x-axis label to "CO2 (ppm)"
ax.set_xlabel('CO2 (ppm)')

# Set the y-axis label to "Relative temperature (C)"
ax.set_ylabel('Relative temperature (C)')

plt.show()

fig, ax = plt.subplots()

# Add data: "co2", "relative_temp" as x-y, index as color
ax.scatter(climate_change['co2'], climate_change['relative_temp'],
c=climate_change.index)

# Set the x-axis label to "CO2 (ppm)"
ax.set_xlabel('CO2 (ppm)')

# Set the y-axis label to "Relative temperature (C)"
ax.set_ylabel('Relative temperature (C)')

plt.show()

#### Preparing your figures to share with others ####
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.plot(seattle_weather['MONTH'], seattle_weather['MLY-TAVG-NORMAL'])
ax.plot(austin_weather['MONTH'], seattle_weather['MLY-TAVG-NORMAL'])
ax.set_xlabel('Time (months)')
ax.set_ylabel('average temperature (Farenheit degrees)')
plt.show()

# Choosing a style
plt.style.use('ggplot')
fig, ax = plt.subplots()
ax.plot(seattle_weather['MONTH'], seattle_weather['MLY-TAVG-NORMAL'])
ax.plot(austin_weather['MONTH'], seattle_weather['MLY-TAVG-NORMAL'])
ax.set_xlabel('Time (months)')
ax.set_ylabel('average temperature (Farenheit degrees)')
plt.show() 

# Back to default
plt.style.use('default')

# Matplotlib contains different visualization styles
# The 'bmh' style
plt.style.use('bmh')

# The seaborn style
plt.style.use('seaborn-colorblind')

# Guidelines for choosing plotting style
# depends on your goal
# dark backgrounds are usually less visible and not recommended generally
# if color is important, consider choosing coloblind-friendly options
# 'seaborn-coloblind' or 'tableau-colorblind10'
# if you think that someone will want to print your figure, use less ink (avoid colored backgrounds)
# if it will be printed in black-and-white, use the 'grayscale' style

#### Sharing your visualizations with others ####
# a figure to share
fig, ax = plt.subplots()
ax.bar(medals.index, medals['Gold'])
ax.set_xticklabels(medals.index, rotation=90)
ax.set_ylabel('Number of medals')
plt.show()

# saving the figure to file
fig, ax = plt.subplots()
ax.bar(medals.index, medals['Gold'])
ax.set_xticklabels(medals.index, rotation=90)
ax.set_ylabel('Number of medals')
plt.show()
fig.savefig('gold_medals.png')
ls # we can call the unix ls function, which gives us a listing of the files in the present working directory

# different file formats
# provides lossless compression of your image
# means the image will retain high quality, but will also take up relatively large amounts of diskspace or bandwidth
# if the image is going to be on a website, for ex, you might want to choose the jpg format used here b/c of it uses lossy compression, and can be used to create figures that take up less diskspace and less bandwidth
# you can also control how small the resulting file will be, and the degree of loss of quality, by setting the quality key-word argument
fig.savefig('gold_medals.jpg', quality=50)
fig.savefig('gold_medals.jpg') 
