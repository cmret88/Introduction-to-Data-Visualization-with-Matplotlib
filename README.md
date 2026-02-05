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
