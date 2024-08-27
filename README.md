# Python_Data_Analysis

1, Graph for percentage of missing values under each column

(missing_values[:20]*100).plot(kind="bar", ylabel="Percentage(%)")

![image](https://github.com/user-attachments/assets/ab9fe6be-6291-48fa-912d-8f48028d9523)

2, Identifying Top 20 cities by accident

cities = df.City.unique()
len(cities)
#Listing out the top 20 cities by accident
count_of_cities = df.City.value_counts()
count_of_cities[:20]

![image](https://github.com/user-attachments/assets/3bca3d6c-2caa-4b06-b642-da603333c8d5)

Visualization for the top 20 cities by accident
count_of_cities[:20].plot(kind="area", color='lightblue')

![image](https://github.com/user-attachments/assets/5eb0b585-fac4-41f9-9e1b-14d4bef727ad)


3, Accident for each cities

# x-axis = no of accident count by cities, Y-axis = no of cities
sns.set_style("darkgrid")
#plt.style.use("dark_background")
sns.histplot(count_of_cities,log_scale=True,color='darkcyan'

![image](https://github.com/user-attachments/assets/fde07ccd-827b-4739-8682-6962e31643b0)

4, count_of_cities[count_of_cities == 1]  #1023 cities which has just 1 accident , there are 12655 cities which has > 1 accident

![image](https://github.com/user-attachments/assets/3660d736-0613-4298-91fa-95d78dd0d14d)

5, Seperating the city by high and low accident count

high_rate_cities = count_of_cities[count_of_cities >=1000]
low_rate_cities = count_of_cities[count_of_cities < 1000]
high_rate_cities

![image](https://github.com/user-attachments/assets/c98d1915-1893-490f-ab2a-bd6b0ac364ce)

#Getting the percentage of accident oh high_rate_cities
percent_high=(len(high_rate_cities) / len(cities))*100
percent_high
sns.distplot(high_rate_cities,color='purple')

![image](https://github.com/user-attachments/assets/57e3c0d3-6d8a-4a6b-a4e5-4395ca1136ed)

low_rate=(len(low_rate_cities) / len(cities))*100
low_rate
91.0885298632941

sns.distplot(low_rate_cities,color='midnightblue')

![image](https://github.com/user-attachments/assets/f6d4b391-4975-4d17-b81a-2f5ee133f5ac)

6, Accident Trends

#We used the "norm_hist=True" toget the percentage of teh values on the y axis
hist_data = sns.distplot(hours,bins = 24,kde = False, norm_hist=True)
for patch, left_bin in zip(hist_data.patches, hist_data.patches):
    for patch in hist_data.patches:
        bin_center = patch.get_x() + patch.get_width() / 2  # Find the center of the bin
        if (6 <= bin_center < 9) or (14 <= bin_center < 19):
            patch.set_facecolor('darkblue')
        else:
            patch.set_facecolor('lightblue')

![image](https://github.com/user-attachments/assets/35a94282-6103-4f7b-84dd-1f3052db541f)

7, #During weekends no of accidents were lower as compared to the weekdays 

weeks = sns.distplot(day,bins = 7,kde = False, norm_hist=True)
patches = weeks.patches
for i, patch in enumerate(patches):
    if i < 5:
        patch.set_facecolor('skyblue')   # First five bins (0 to 4)
    elif i == 5:
        patch.set_facecolor('cornflowerblue')  # Sixth bin
    elif i == 6:
        patch.set_facecolor('dodgerblue')    # Seventh bin

![image](https://github.com/user-attachments/assets/e8de1d39-5718-4d1f-97e5-b8d1607eef1c)

8. Accidents combined on saturday and sunday to compare it with monday¶

ss = sns.distplot(sunSats.dt.hour,bins = 24,kde = False, norm_hist=True)
for patch, left_bin in zip(hist_data.patches, ss.patches):
    for patch in ss.patches:
        bin_center = patch.get_x() + patch.get_width() / 2  # Find the center of the bin
        if (6 <= bin_center < 9) or (14 <= bin_center < 17):
            patch.set_facecolor('indigo')
        else:
            patch.set_facecolor('mediumpurple')

![image](https://github.com/user-attachments/assets/9562e7c1-2d09-4b65-9dd5-2c91b6edbc3f)

9, Accidents monthly wise from 2016 - 2023

#The rate of accident is higher over the beginning and the ending of the year may be due to the festive season
mn = sns.distplot(month,bins = 12,kde = False, norm_hist=True)
for patch, left_bin in zip(hist_data.patches, mn.patches):
    for patch in mn.patches:
        bin_center = patch.get_x() + patch.get_width() / 2  # Find the center of the bin
        if (10 <= bin_center < 12) or (1 <= bin_center < 2):
            patch.set_facecolor('darkcyan')
        else:
            patch.set_facecolor('paleturquoise')

![image](https://github.com/user-attachments/assets/91734045-eb61-4119-8909-969f3bd1d89a)

10, Comparision of four years

yr = sns.distplot(year_of_4.dt.month,bins = 12,kde = False, norm_hist=True)
for patch, left_bin in zip(hist_data.patches, yr.patches):
    for patch in yr.patches:
        bin_center = patch.get_x() + patch.get_width() / 2  # Find the center of the bin
        if (11 <= bin_center < 12) or (1 <= bin_center < 3):
            patch.set_facecolor('darkcyan')
        else:
            patch.set_facecolor('paleturquoise')

![image](https://github.com/user-attachments/assets/7e261528-8c72-4cfc-9c9d-fdfa6bbe7953)

11, To know the spread of accident data across the US using the scatter plot to figure it out

lat = df.Start_Lat
lng = df.Start_Lng
sns.scatterplot(x=lng,y=lat,color='slateblue')

![image](https://github.com/user-attachments/assets/cbb4d623-ef43-4c0d-868d-a353480087dc)

Analysis

![image](https://github.com/user-attachments/assets/df4a1764-52df-4d15-8e33-81805c7b9485)

![image](https://github.com/user-attachments/assets/c174e336-dd60-4374-94e1-b9a02ab7d0e7)









