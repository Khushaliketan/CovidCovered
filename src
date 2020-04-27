#python3

import folium
import pandas as pd

dataset = pd.read_excel('Covid Care-Testing-Collection Centres Kerala.xlsx')

#understanding the dataset
dataset.info()

dataset.columns

dataset.head()

#location of each center strored in 'location'
location = dataset[['Lattitude', 'Longitude']]

type(location)

#to convert dataframe into list
location = location.values.tolist()

#Creating the map
kmap = folium.Map(location=[11.281728,75.755295], zoom_start=7)

#Marker Atrribute fucntion of each of the three kinds of centers.
def markerAttr(i,color,ic):
    folium.Marker(location=point,
                 popup=dataset['Name'][i],
                 icon=folium.Icon(color=color, icon=ic, prefix='fa'),
                 ).add_to(kmap)

#Iterating through the dataset
i=0
for point in location:
    if dataset['CentreType'][i]=='Care':
        markerAttr(i,'darkblue','home')
    elif dataset['CentreType'][i]=='Testing':
        markerAttr(i,'red','map-pin')
    elif dataset['CentreType'][i]=='Collection':
        markerAttr(i,'green','plus-square')
    i=i+1


#adding the draggable legend -> Made with jQuery
from branca.element import Template, MacroElement

template = """
{% macro html(this, kwargs) %}

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>jQuery UI Draggable - Default functionality</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">

  <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
  <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
  
  <script>
  $( function() {
    $( "#maplegend" ).draggable({
                    start: function (event, ui) {
                        $(this).css({
                            right: "auto",
                            top: "auto",
                            bottom: "auto"
                        });
                    }
                });
});

  </script>
</head>
<body>

 
<div id='maplegend' class='maplegend' 
    style='position: absolute; z-index:9999; border:2px solid grey; background-color:rgba(255, 255, 255, 0.8);
     border-radius:6px; padding: 10px; font-size:14px; right: 20px; bottom: 20px;'>
     
<div class='legend-title'>Legend (draggable!)</div>
<div class='legend-scale'>
  <ul class='legend-labels'>
    <li><span style='background:red;opacity:0.7;'></span>Testing_Centre</li>
    <li><span style='background:blue;opacity:0.7;'></span>Care_Centre</li>
    <li><span style='background:green;opacity:0.7;'></span>Collection_Centre</li>

  </ul>
</div>
</div>
 
</body>
</html>

<style type='text/css'>
  .maplegend .legend-title {
    text-align: left;
    margin-bottom: 5px;
    font-weight: bold;
    font-size: 90%;
    }
  .maplegend .legend-scale ul {
    margin: 0;
    margin-bottom: 5px;
    padding: 0;
    float: left;
    list-style: none;
    }
  .maplegend .legend-scale ul li {
    font-size: 80%;
    list-style: none;
    margin-left: 0;
    line-height: 18px;
    margin-bottom: 2px;
    }
  .maplegend ul.legend-labels li span {
    display: block;
    float: left;
    height: 16px;
    width: 30px;
    margin-right: 5px;
    margin-left: 0;
    border: 1px solid #999;
    }
  .maplegend .legend-source {
    font-size: 80%;
    color: #777;
    clear: both;
    }
  .maplegend a {
    color: #777;
    }
</style>
{% endmacro %}"""

macro = MacroElement()
macro._template = Template(template)

#adding the legend child to map
kmap.get_root().add_child(macro)

#finally, display it!
kmap

#Save
kmap.save('Covid19_Important_Centres_In_Kerala.html')
