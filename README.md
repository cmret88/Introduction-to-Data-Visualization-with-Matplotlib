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
