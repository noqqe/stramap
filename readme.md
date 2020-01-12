# stramap

I'd like to plot all my cycling activities per year (as well as all the years combined) to one single map so
that I can see my progress over the years.

stramap takes the input of the Strava export from your profile and plots all
gpx tracks to an OSM Map and results to an index.html file.

![logo](demo.png)

# Strava Data

To get your strava data, go to 'Account' and 'Delete and Backup Account'. You
later recieve an email with a zip in it, that contains a folder called
'activities'

In my export from strava (been there since 2014 with imports from runkeeper)
live a couple of different formats, so we need to do a little conversion
work upfront

* gpx (yay)
* gpx.gz (okay)
* tcx (home trainer data, we can just ignore this)
* fit (binary format)
* fit.gz (binary format)

In order to work with the data we convert everything we can to `gpx`

```
cd activities/
unzip  *.gz
for x in *.fit ; do gpsbabel -i garmin_fit -f $x -o gpx -F $x.gpx ; done
```

