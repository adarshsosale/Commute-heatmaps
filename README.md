# Location livability index - Commute heatmaps
Simple script to sample commute time from [Google Directions API](https://developers.google.com/maps/documentation/directions/) given target address.
These samples are then interpolated to generate a dense commute time heatmap that can be overlap to any map, eg. Google Maps.

## Dependencies

Python Imaging Library is the only dependency at the moment. The instructions to be followed to install it on your specific platform can be found [here](http://www.pythonware.com/products/pil/).

## Usage

1. Generate your own [Google Directions API key](https://developers.google.com/maps/documentation/directions/).
2. Create a file simply named `key` in the main project folder with the only your key in it.
3. Set the coordinate of the region you want to sample from in `sample_distances.py`. 
4. Run `sample_distances.py` to start sampling. Results will be stored in `samples.txt`.
5. Run `draw_heatmap.py`to generate the heatmaps.



## Samples

By default this script samples random locations within a given area and provide commute time with public transport. Each location is sampled 2 times at different random times between 7AM and 5PM.
The number of times a given location is sampled is set as a variable. However, unless the key is changed dynamically, the maximum samples allowed by the API is 2500 per day.

Two different set of figures are generated:

-`best`: the mean commute time assuming the departure is at the best time to avoid waiting for a bus, tram or train at its stop.

-`random`: the mean commute time assuming departure at random time, ie. leaving from home without taking into account the public transport timetable.



## Insights

Areas served by fast but low-frequency means of transportation are those where the difference between the two metric is more evident. 

There are a lot of interesting insights that are derived from the map.

1. There are pockets within cities in general, where the public transport networks is strong and the time required to commute to the target is lower than in the surroundings.
2. There are also pockets that have poor transport access and have relatively high commute times. This is more common in large developing cities that have expanded in a rapid, unplanned manner.
3. The way large water bodies that separate large cities around the world is very interesting. In developed cities like Zurich and London, rivers generally act just as a minor hinderance.
4. The commute mode can be changed from public transport to an own vehicle. In developing cities, the change in the heatmap is found to be more stark than in developed ones.
