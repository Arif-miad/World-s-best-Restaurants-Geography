
<div align="center">
      <H1> World-s-best-Restaurants-Geography</H1>
<H2>
</H2>  
     </div>

<body>
<p align="center">
  <a href="mailto:arifmiahcse952@gmail.com"><img src="https://img.shields.io/badge/Email-arifmiah%40gmail.com-blue?style=flat-square&logo=gmail"></a>
  <a href="https://github.com/Arif-miad"><img src="https://img.shields.io/badge/GitHub-%40ArifMiah-lightgrey?style=flat-square&logo=github"></a>
  <a href="https://www.linkedin.com/in/arif-miah-8751bb217/"><img src="https://img.shields.io/badge/LinkedIn-Arif%20Miah-blue?style=flat-square&logo=linkedin"></a>

 
  
  <br>
  <img src="https://img.shields.io/badge/Phone-%2B8801998246254-green?style=flat-square&logo=whatsapp">
  
</p>

***About Dataset



This dataset contains the lists of World’s 50 Best Restaurants, from 2002 to 2023.

The World’s 50 Best Restaurants, established in 2002, is an annual list and awards ceremony that celebrates global culinary diversity, showcasing top restaurants and culinary trends through a voting process involving over 1,000 culinary experts from 27 regions.


```python
leaders = data[data['rank'] == 1]

plt.figure(figsize=(12, 8))

sns.scatterplot(x='year', y='restaurant', data=leaders, s=150, color="red")

plt.title('Ranking leaders by year', fontsize=16)
plt.xlabel('Year', fontsize=14)
plt.ylabel('Restaurant', fontsize=14)
plt.xticks(rotation=45)
plt.grid(True)
plt.tight_layout()
plt.show()

top_10 = data[data['rank'] <= 10]

top_10_countries = top_10['country'].value_counts().reset_index()
top_10_countries.columns = ['country', 'count']


plt.figure(figsize=(10, 6))
sns.barplot(x='count', y='country', data=top_10_countries, palette='Greens_d')
plt.title('Countries with the largest number of restaurants in the top 10', fontsize=14)
plt.xlabel('Number of restaurants', fontsize=12)
plt.ylabel('Country', fontsize=12)
plt.xticks(rotation=90)
plt.show()
map_world = folium.Map(location=[20,0], zoom_start=2)

for index, row in data.iterrows():
    folium.Marker(
        location=[row['lat'], row['lng']],
        popup=f"{row['restaurant']} ({row['country']})"
        ).add_to(map_world)

map_world.save("restaurants_map.html")

map_world
```
![image](https://github.com/Arif-miad/World-s-best-Restaurants-Geography/blob/main/__results___12_0.png)
