Introduction to GIS for the Social Sciences
===========================================

This tutorial uses QGIS 3 to teach the basics of desktop GIS for the
Social Sciences, with an emphasis on acquiring census data, mapping
census tracts, and generating a map.

Workshop Preparation
--------------------

You should download and install [QGIS version
3.14](https://qgis.org/en/site/forusers/download.html) or higher to your
computer.

The datasets for the workshop are available in this [Box Folder
Online](https://ucla.box.com/s/98xzkv5rj5fcszn5blhi5vbsrtwwlj2z).

Download all the files and extract them.

Workshop Aims
-------------

This beginner-level workshop will focus upon the fundamental concepts
and skills needed to use Geographic Information Systems (GIS) software
for the exploration and analysis of U.S. Census datasets with spatial
attributes using the QGIS platform.

No prior experience QGIS or other GIS software is required.

By the end of this workshop, you will be able to:

-   Define basic GIS geospatial concepts and terminology.

-   Know the about different type of data sets

-   Understand where to find Census data on the web

-   Know how to add data to a QGIS project

-   Find the attributes of your data in QGIS

-   Perform basic selections and queries in QGIS

-   Stylize a map using different data types in QGIS

-   Export a map in QGIS

Introduction to GIS
===================

What is GIS? Depending on who you ask, GIS has two meanings:

Geographic Information System typically refers to applications and
software that is used to create spatial data and to investigate spatial
relationships between that data.

Geographic Information Science is the framework we use to ask questions
about the spatial relationship between data.

For example, predicting the effects of climate change (rising
sea-levels) on low laying areas (elevation) would be an application of
Geographic Information Science, while the software to do the predictions
would be an example of a Geographic Information System.

In short:

![](./images//media/image1.png){width="3.1597222222222223in"
height="1.312037401574803in"}

Data Types
----------

There are two key distinction between data types, spatial or non-spatial
data.

Spatial data is data that already contains geographic information.

Common file types are the following:

-   **Shapefiles:** .zip (these are made up of 5 files, and the .shp is
    commonly used to identify them)

-   **KML files:** .kml, .kmz

-   **GeoJSON files:** .geojson

-   **JPG files**: .jpg\*

Non-spatial data is data that has no geographic information.

Common non-spatial data are the following:

-   **Excel Spreadsheets**: .xlsx, .xls

-   **Comma/Table Separated Value files**: .csv, .tsv

-   **JSON files**: .json

-   **dBase database file**: .dbf

When non-spatial data has geographic attributes, like zipcodes,
addresses, city names, or even latitude/longitude coordinates it can be
turned into spatial data. The distinction is that non-spatial data will
only show up as tables in GIS applications.

On the other hand, spatial data that has data attributes can be turned
into a non-spatial data type by saving/exporting its data as tables. The
following graphic summarizes this relationship:

![](./images//media/image2.png){width="6.552777777777778in"
height="2.880417760279965in"}

Spatial Data Formats
--------------------

There are several data spatial data models that you may encounter as you
work with geo data. Geodata formats are commonly divided into two types,
vector data or a raster data. In GIS, discrete data means that the data
has a fixed location. Continuous data in GIS does not have well defined
or no boundary at all, the most common example is elevation. The graphic
below shows how vector data and raster data formats can represent
continuous or discrete data:

![alt text](./images//media/image3.png){width="3.0625in"
height="3.0262051618547683in"}

Spatial Data Types (Source: Michele Tobias, UC Davis)

The graphic also illustrates how certain vector data is often better
suited for discrete data, while raster data is often better used for
continuous data. Let's go into a little more detail about each!

### Vector Data

Vector data represents discrete objects in the real world with points,
lines, and polygons in the dataset.

If you were to draw a map to your house for a friend, you would
typically use vector data - roads would be lines, a shopping center
included as an important landmark might be a rectangle of sorts, and
your house might be a point (perhaps represented by a star or a house
icon).

### Raster Data

Raster data represents continuous fields or discrete objects on a grid,
storing measurements or category names in each cell of the grid.

Digital photos are raster data you are already familiar with. If you
zoom in far enough on a digital photo, you\'ll see that photo is made up
of pixels, which appear as colored squares. Pixels are cells in a
regular grid and each contains the digital code that corresponds to the
color that should be displayed there.

You may be surprised to see jpgs listed as a data type that you may have
thought to be non-spatial, but satellite imagery is commonly stored in
photo formats.

Introduction to GIS for the Social Sciences
-------------------------------------------

Now that we have a good understanding of geospatial data, we can explore
the GIS connection to the social sciences.

Geography is divided into physical geography (natural systems) and human
geography (human-made systems). The social sciences sit within
human-made systems and the data here is often captured in specific
units. Such as number of people living in a specific city or the
language spoken in a country. Thusly, most of the data we will encounter
will be discrete.

Another common example is the following election result map which shows
the number of people from each state that voted for either Clinton or
Trump in the 2016 general election.

![](./images//media/image4.png){width="4.716709317585302in"
height="3.111111111111111in"}

Source: [New York Times,
2016](https://www.nytimes.com/elections/2016/results/president)

The states themselves are the boundaries, even though the data is
collected at smaller levels.

How is that possible? The answer is geographical hierarchy.

### 

### Geographic Hierarchy

Move over Aristotle: The **sum** is the whole of its parts!

The first law of Geography (and perhaps only) is "**everything is
related to everything else, but nearer things are more related than
distant things.**" When thinking about human data, there are many
different units, countries, states, cities, and even households.
Whenever this data is being summarized to larger geographies, as long as
the smaller boundaries do not overlap then you can do so. However, this
does not mean it is always safe to do so, why?

Keeping the first law of geography in mind, when you summarize smaller
data to larger geographies (i.e. going from cities to a state), the
nearer things become less related because they are summarized to a
larger geographic relation. Let's return to the election map above, but
break it down into counties to see how the summing of the data changed
spatial relationships.

![](./images//media/image5.png){width="6.5in"
height="3.640972222222222in"}

How does this map compare to the previous map?

![](./images//media/image4.png){width="6.493055555555555in"
height="3.5259623797025372in"}

For one thing, you can see that a state like Arizona is not completely
red and has quite a bit of democratic voters. This is possible, because
the geographic hierarchy is preserved when the data from the counties is
summarized to the state level.

Below is an example of how the United States Census Bureau has developed
a hierarchal geography:

![](./images//media/image6.png){width="3.763472222222222in"
height="3.8055555555555554in"}

The Federal Information Processing Standards (FIPS) codes represents
this in numerical format:

\[STATE\] + \[COUNTY\] + \[CENSUS TRACT\] + \[CENSUS BLOCK GROUP\]\
For example:\
06 + 037 + 2653 + 01 or 06037265301, which is UCLA's census tract.

When data is organized in this way it can readily summarized, since the
smaller units make up the larger units. For example, demographic
information that is collected at the smaller Census Tract level can be
easily aggregated to answer questions at the city or state level.
Questions such as "how many Asians are there in California?" are readily
answerable. But the voting data that was collected at the voting
precinct level, the summarization could occur at the state level because
all the units fell within a particular state and it did not overlap. If
you were to combine the voting data with a bigger geography that causes
boundaries to overlap, then data will be double counted and will cause
problems (and headaches!)

What other ways could voter data be summarized to?

Voting data can also be summarized at the county level, since counties
do not overlap and these are still bigger than the precincts. When
trying to aggregate data to the census tracts a major problem occurs,
some precincts will overlap with many different census tracts! A special
type of analysis, called a "weighted-merge" will need to be done in
order to distribute the votes across census tracts accurately.

Now that we have a better understanding of geospatial datasets, how it
relates to the social sciences, and some of the problems associated with
them, we can finally start to utilize spatial data.

Finding data
------------

In this workshop, we will be answering the following question:

Research Question: Which areas in Los Angeles have more than 25% of
their population living in poverty?

We will be using the following data:

-   Los Angeles 2010 Census Tracts

-   County Boundaries

We are using the Census Tracts because those are how demographic data is
collected in the United States.

Data for mapping in the social sciences will commonly be found as
standalone tables or vector data, and the best way to find these data is
from authoritative sources, like the government, news organizations, and
research groups.

Below is a table compiled from the UCLA Library detailing other data
sources:

+-----------------------------------+-----------------------------------+
| Entity                            | Links                             |
+===================================+===================================+
| California Census Research Data   | <http://www.ccrdc.ucla.edu/>      |
| Center (CCRDC)                    |                                   |
+-----------------------------------+-----------------------------------+
| UCLA California Center for        | [Social Sciences Data             |
| Population Research (CCPR)        | Archive](https://ccpr.ucla.edu/se |
|                                   | rvices/data/),                    |
|                                   | including                         |
|                                   |                                   |
|                                   | -   [German Federal Employment    |
|                                   |     Agency (FDZ) Research Data at |
|                                   |     CCPR](https://ccpr.ucla.edu/s |
|                                   | ervices/data/census-data/fdz-data |
|                                   | /)                                |
|                                   |                                   |
|                                   | -   [Ready Data                   |
|                                   |     Services](https://ccpr.ucla.e |
|                                   | du/services/data/ready-data/)     |
|                                   |                                   |
|                                   | -   [Social Sciences Data         |
|                                   |     Archives](https://ccpr.ucla.e |
|                                   | du/services/data/social-sciences- |
|                                   | data-archives/)                   |
|                                   |                                   |
|                                   | -   [[CCPR                        |
|                                   |     Statistical Services]{.underl |
|                                   | ine}](https://ccpr.ucla.edu/servi |
|                                   | ces/statistics-and-methods-core-m |
|                                   | ission/)                          |
|                                   |                                   |
|                                   | -   [Demographic Data             |
|                                   |     Sources](https://ccpr.ucla.ed |
|                                   | u/services/data/demographic-data- |
|                                   | sources/)                         |
+-----------------------------------+-----------------------------------+
| UCLA Library                      | The library licenses many         |
|                                   | databases that contain datasets.  |
|                                   | [See the                          |
|                                   | list.](http://guides.library.ucla |
|                                   | .edu/az.php?t=3849&_ga=1.22561499 |
|                                   | 4.929300897.1454461090)           |
|                                   |                                   |
|                                   | Also see:                         |
|                                   |                                   |
|                                   | Social Sciences Data Archive -    |
|                                   | Data Portals:                     |
|                                   |                                   |
|                                   | > <http://www.library.ucla.edu/so |
|                                   | cial-science-data-archive/data-po |
|                                   | rtals>                            |
+-----------------------------------+-----------------------------------+

Source: UCLA Library, 2020

Getting down with geodata hubs
------------------------------

Geodata portals are other places where spatial data sets can be found.
The Los Angeles County operates a geodata portal that uses the ESRI
Geohub tool, and we will navigate to it below:

<https://egis-lacounty.hub.arcgis.com/>

1.  Click the search box and type in "**Population Census Tract**"

    ![](./images//media/image7.png){width="6.5in"
    height="2.2270833333333333in"}

2.  Click on "**Population and Poverty by Census Tract**"

    ![](./images//media/image8.png){width="6.5in"
    height="2.2270833333333333in"}

3.  Before downloading anything, we should check the see if this data is
    worth it, so click on "More" under "General Attribute Information"

    ![](./images//media/image9.png){width="5.931470909886264in"
    height="4.423611111111111in"}

4.  Scroll down to see the table that says, "**population below federal
    poverty level**"

    ![](./images//media/image10.png){width="4.966188757655293in"
    height="4.048611111111111in"}

5.  Perfect, the data we need is in here:

    1.  **male18a** is the total male population 100% below the Federal
        Poverty Level

    2.  **female18a** is the total female population100% below the
        Federal Poverty Level.

6.  Scroll down the page and find and click "**Download**"

    ![](./images//media/image11.png){width="5.628755468066491in"
    height="2.9027777777777777in"}

Pop-quiz! Which file types are spatial and which are not?

7.  Download the shapefile:

    ![](./images//media/image12.png){width="1.8541666666666667in"
    height="2.816784776902887in"}

8.  Extract the zip file.

    ![](./images//media/image13.png){width="4.444444444444445in"
    height="3.2929735345581803in"}

9.  You should now have a new folder containing the following files:

    ![](./images//media/image14.png){width="6.609791119860017in"
    height="2.048611111111111in"}

**Exercise \#1**

Find and download the County Boundary Layer.

Hint: Search "Boundary"

If you get stuck, feel free to download all of required data from this
[Box Folder
Online](https://ucla.box.com/s/98xzkv5rj5fcszn5blhi5vbsrtwwlj2z).

Start QGIS & Open a New Project
===============================

10. Start QGIS in the way you typically open any program on your
    particular computer\'s operating system.

11. Click on the "New file" on the top right corner to start a new
    project.

    ![](./images//media/image15.png){width="6.182925415573053in"
    height="3.5208333333333335in"}

12. Let's get acquainted with the default layout of QGIS:

    3.  **Map panel**: Where the layers for the map will be displayed

    4.  **Layers panel**: Where the layers can be reorganized and
        modified

    5.  **Toolbar**: Where you can quickly change tools to interact with
        the map

    6.  **Processing Panel**: Advanced tools for interacting with layers

        ![](./images//media/image16.png){width="5.826388888888889in"
        height="4.076604330708661in"}

13. Add the downloaded data set by going to the Toolbar and then
    "Layer" \>\> "Add Vector Data":

    ![](./images//media/image17.png){width="6.495271216097988in"
    height="4.1875in"}

14. Click on the "..." to browse for the shapefile that we downloaded:

    ![](./images//media/image18.png){width="5.912465004374453in"
    height="3.3194444444444446in"}

15. Locate the file and click "**Open**".

16. Click "**Add**"

    ![](./images//media/image19.png){width="6.06533573928259in"
    height="3.3819444444444446in"}

17. Notice that the dataset was added to the Layer Panel and then Map
    Panel at the same time:

    ![](./images//media/image20.png){width="6.8148370516185475in"
    height="4.75in"}

### Attribute Tables: Taking a closer look at our data

The value of GIS data is that it has various information connected to
it. We can examine and interrogate this data by opening the layer's
"**Attribute Table**."

18. Let's check what data we have by right clicking on the layer:

    ![](./images//media/image21.png){width="3.9748753280839897in"
    height="2.9305555555555554in"}

19. Go to "**Open Attribute Table**" to open the data:

    ![](./images//media/image22.png){width="4.694444444444445in"
    height="5.340986439195101in"}

20. A window should open up with the data in columns and rows:

    ![](./images//media/image23.png){width="6.876498250218723in"
    height="3.0694444444444446in"}

21. The "green" box is the location of our cursor in the data and is
    useful to find where we are in our data set:

    ![](./images//media/image24.png){width="5.152777777777778in"
    height="3.1725349956255466in"}

Let's answer the following.

Spatial Question \#1:

What are the Top 10 Census Tracts with males in Los Angeles County?

22. We can quickly sort the rows by the column by clicking on them, so
    for our query, we will click on "male":

    ![](./images//media/image25.png){width="6.5in"
    height="2.901388888888889in"}

    Notice how an arrow appears and the data begins at 0 now.

23. Click "**male**" once again to sort by descending:

    ![](./images//media/image26.png){width="5.243055555555555in"
    height="3.243507217847769in"}

24. Your data table should look like the following with the arrow facing
    downwards:

    ![](./images//media/image27.png){width="4.791666666666667in"
    height="2.321114391951006in"}

25. Click on the "1" to highlight that feature:

    ![](./images//media/image28.png){width="3.5694444444444446in"
    height="2.631900699912511in"}

26. Check the map to see what happened:

    ![](./images//media/image29.png){width="5.505465879265092in"
    height="4.305555555555555in"}

    Census tracts are small, so they are pretty hard to see, especially
    with these outlines! Don't worry though, we'll get to making the map
    prettier later. For now, let's return to answering our spatial
    query!

27. Let's go back to our table and from the "1" on the left, that down
    to "10", this effectively answers our question:

    ![](./images//media/image30.png){width="5.940574146981628in"
    height="3.1180555555555554in"}

28. Check the map to see what happened:

    ![](./images//media/image31.png){width="4.458333333333333in"
    height="3.486645888013998in"}

29. Notice that the selection of the data has also appeared on the map
    as yellow highlights:

    ![](./images//media/image32.png){width="6.5in"
    height="5.083333333333333in"}

30. While this method of filtering is quick, it does have drawbacks
    because requires scrolling through the data set.

31. Clear our current selection by clicking on the "**Clear Selection**"
    button:

    ![](./images//media/image33.png){width="5.438917322834645in"
    height="3.8333333333333335in"}

### Creating Fields

Returning to our research question, "which census tracts have more than
25% of the population living in poverty," the fields that we need for
our analysis do not exist, so we have to create them!

Since, our data set only has male and female population, we can add
those up to create the total population. The same applies for the
population in poverty, too. In order to generate these fields, we will
need to create those fields using the "**Field Calculator**". To create
the "**total population**" field we need to add the **male** and
**female** fields, to create the "total population under the 100%
Federal Poverty Line" field we will need to add **male18a** and
**female18a**.

32. Since we are going to be editing our data, we need to toggle editing
    mode by clicking on the **pencil** icon:

    ![](./images//media/image34.png){width="4.847222222222222in"
    height="2.354080271216098in"}

33. Click on "**Field Calculator**"

    ![](./images//media/image35.png){width="5.361111111111111in"
    height="2.2687182852143484in"}

34. Create a new field with the following:

    7.  **Output field name**: TOTAL\_POP

    8.  **Output field type**: "Whole number (integer)"

    9.  **Expression**: "**male**" + "**female**"

> ![](./images//media/image36.png){width="4.4058169291338585in"
> height="3.236111111111111in"}
>
> To avoid misspelling, you can type "**male**" in the search on the
> right and it will filter the fields for you, this will allow you to
> double click on the field to add into the expression:
>
> ![](./images//media/image37.png){width="4.686640419947507in"
> height="3.451388888888889in"}

35. When your fields look like the following, click on "**OK**" to
    create the field:

    ![](./images//media/image38.png){width="5.795405730533683in"
    height="4.3125in"}

36. Let's add the next field called **POVERTY\_POP**, which will be the
    combination of **male18a** and **female18a**:

    10. **Output field name**: POVERTYPOP

    11. **Output field type**: "Whole number (integer)

    12. **Expression**: **"male18a"** + **"female18a"**

![](./images//media/image39.png){width="5.611111111111111in"
height="4.132200349956255in"}

Recall that **male18a** and **female18a** are stated from the Los
Angeles Geohub as " Population 100% Federal Poverty Level"

The last field we will calculate is the proportion of the population
that is under poverty line which is the number of people in poverty
(**POVERTYPOP**) divided by the total population (**TOTAL\_POP**). The
field will be called, **POVERTY\_RA**, for poverty ratio.

37. The "**Field Calculation**" should look like the following:

    13. **Output field name**: POVERTY\_RA

    14. **Output field type**: "Decimal number (real)"

    15. **Expression**: "**POVERTYPOP**" / "**TOTAL\_POP**"

![](./images//media/image40.png){width="5.12909886264217in"
height="3.7777777777777777in"}

38. Now that we have our fields ready, let's filter out Census Tracts
    with no population.

39. Rather than do a quick sort, locate the toolbar, and click on the
    filter button:

    ![](./images//media/image41.png){width="5.941041119860017in"
    height="3.4305555555555554in"}

40. Scroll down to the total population field we calculated,
    "**TOTAL\_POP**"

41. Click on "**Exclude Field**" next to "**TOTAL\_POP**":

    ![](./images//media/image42.png){width="6.125in"
    height="4.039489282589677in"}

42. Change it to "**Greater than**":

    ![](./images//media/image43.png){width="6.37471019247594in"
    height="4.416666666666667in"}

43. Next to "TOTAL\_POP", enter "**0**":

    ![](./images//media/image44.png){width="6.125in"
    height="4.012659667541557in"}

44. Scroll to the bottom of the window and choose "**Select Features**"

    ![](./images//media/image45.png){width="6.5in"
    height="4.258333333333334in"}

45. Select the table icon to return to the table view:

    ![](./images//media/image46.png){width="5.895833333333333in"
    height="3.6546620734908135in"}

46. Notice that the "Selected" on the top has changed to reflect the
    number of records selected:

    ![](./images//media/image47.png){width="6.5in"
    height="4.315277777777778in"}

47. You can view only selected records by clicking on the lower right
    and going to "**Selected Records"**.

    16. ![](./images//media/image48.png){width="5.670668197725284in"
        height="1.4375in"}

    17. ![](./images//media/image49.png){width="5.6486646981627295in"
        height="1.4236111111111112in"}

    18. ![](./images//media/image50.png){width="5.711297025371828in"
        height="3.7916666666666665in"}

    19. Save our edits by clicking on the disk icon:

        ![](./images//media/image51.png){width="5.670138888888889in"
        height="1.2273458005249345in"}

    20. Stop editing by clicking on the pencil icon:

        ![](./images//media/image52.png){width="5.639139326334208in"
        height="1.2222222222222223in"}

Saving datasets
---------------

We can save the records we selected! In doing so, we can save it as a
shapefile (a spatial data type) or as a CSV file (a non-spatial dataset)
that we can use in other software.

### Exporting a Shapefile:

48. With the records still selected, right click on the
    "**Population\_and\_Poverty\_by\_Census\_Tract**" layer:

    ![](./images//media/image53.png){width="5.868055555555555in"
    height="4.078172572178477in"}

49. Click on "**Save Selected Data Set as...**"

    ![](./images//media/image54.png){width="4.503918416447944in"
    height="4.610464785651794in"}

50. Choose the "**ESRI Shapefile**" format:

    ![](./images//media/image55.png){width="3.341780402449694in"
    height="3.8402777777777777in"}

51. For File name, be sure to click on the **"..."** and save your file
    in an accessible location.

    ![](./images//media/image56.png){width="4.139455380577428in"
    height="4.756944444444445in"}

52. Click on "**Select fields to export and their export options**"

    ![](./images//media/image57.png){width="4.292300962379702in"
    height="3.7152777777777777in"}

53. Click on "**Deselect all**" so no columns are selected:

    ![](./images//media/image58.png){width="4.501043307086614in"
    height="3.9375in"}

54. All the checkmarks to the left should disappear:

    ![](./images//media/image59.png){width="4.521104549431321in"
    height="3.9305555555555554in"}

55. Now click the small box to the right of the fields to "check" them
    for exporting.

    21. Check "**tract**" to keep that field:

        ![](./images//media/image60.png){width="3.89367125984252in"
        height="3.4138888888888888in"}

    22. Check "**TOTAL\_POP**", "**POVERTYPOP**", and "**POVERTY\_RA**"
        to keep these fields:

        ![](./images//media/image61.png){width="4.020833333333333in"
        height="4.377567804024497in"}

56. When complete, click on "**OK**" to save the file:

    ![](./images//media/image62.png){width="3.3295920822397203in"
    height="3.625in"}

### Exporting a CSV file

Non-GIS programs will have a hard time working with shapefiles, and the
most basic data file is a text file, so we should also know how to save
files as a CSV!

57. Right click on the new layer we created,
    "**poverty\_in\_la\_county**".

    ![](./images//media/image63.png){width="5.508173665791776in"
    height="4.284722222222222in"}

58. Go to "**Export**" \>\> "**Save Features As..**"

    ![](./images//media/image64.png){width="6.171629483814523in"
    height="3.6319444444444446in"}

59. For Format, choose "**Comma Separated Value \[CSV\]**":

    ![](./images//media/image65.png){width="3.1597222222222223in"
    height="4.816440288713911in"}

60. Save the file in an accessible location and click "OK":

    ![](./images//media/image66.png){width="3.763888888888889in"
    height="4.073790463692038in"}

61. Your "**Layers**" panel should look like the following:

    ![](./images//media/image67.png){width="2.5348523622047243in"
    height="1.5556353893263342in"}

62. Great! Now we know how to save a spatial and non-spatial file type!

63. We can open the attribute for both files in our data layers, and
    doing so for the "**poverty \_in\_la\_county**" gives the following
    window:

    ![](./images//media/image68.png){width="4.0195428696412945in"
    height="1.5972222222222223in"}

### Symbolizing our map

Now that we can export our layers and trim out extra fields, this makes
working with large and complicated data sets a little more manageable
when we are deciding to style our map! Imagine having to constantly
scroll through a list of 20 fields each time you want to change how your
map looks!

64. Right click on "**poverty\_in\_los\_angeles\_county**", and go to
    "**Properties**":

    ![](./images//media/image69.png){width="4.138206474190726in"
    height="3.875in"}

65. On the navigation panel in the properties window, click on
    "**Symbology**"

    ![](./images//media/image70.png){width="5.245964566929134in"
    height="3.6458333333333335in"}

66. Click on the "**Simple Fill**" to open more options:

    ![](./images//media/image71.png){width="6.085320428696413in"
    height="4.229166666666667in"}

67. Click on "**Fill Color**" to open a color picker:

    ![](./images//media/image72.png){width="6.085318241469817in"
    height="4.229166666666667in"}

68. Under "HTML notation" put the following "**\#2774AE**":

    ![](./images//media/image73.png){width="6.076701662292214in"
    height="4.5557895888013995in"}

69. Click "**Ok**"

    ![](./images//media/image74.png){width="5.361111111111111in"
    height="4.000830052493439in"}

70. Outlines are not very helpful when we are zoomed out and have many
    small features, so we will remove them, by clicking "**Stroke
    Style**" and then choosing "**No Pen**":

    ![](./images//media/image75.png){width="5.761111111111111in"
    height="4.075918635170604in"}

71. Click "OK" to apply the changes to the map:

    ![](./images//media/image76.png){width="5.957846675415573in"
    height="4.222222222222222in"}

72. The map should like something like this:

> ![](./images//media/image77.png){width="3.3890627734033245in"
> height="3.1459951881014874in"}

Exercise \#2

Let's apply what we learned and change the symbology of the bottom
layer.

If your map looks the like following, great! I opted to show places with
no people as "white".

![](./images//media/image78.png){width="3.2015529308836395in"
height="3.014044181977253in"}

You successfully were able to apply what we just learned! Our map shows
us places where there are people living in Los Angeles County, but we
can do more and show what the distribution looks like by applying a
colored scale on our maps (also known as a choropleth).

### Advanced Symbology -- A tale of two data types and maps

![](./images//media/image79.png){width="2.763888888888889in"
height="2.1527449693788276in"}![](./images//media/image80.png){width="2.746101268591426in"
height="2.138888888888889in"}

Choropleth maps vs. Categorical maps

A **choropleth map** uses a colored ramp to style to map, typically
having different shades of one color and only works for data that is
numerical. A **categorical map** uses categorical data, often stored as
text fields, to style a map. A categorical map has vastly different
colors for values, and not shades of one color. This is because
categorical data, like name, language spoken, religion, etc. does not
have a numerical association. For example, if someone were to ask you,
"what is the average, median, and mode of city name" and map it, you
would most likely be confused. You could try to convert the categorical
data and get a count of "city names", but to actually treat city name as
a number, is not possible. Similarly, GIS software does not even allow
you to select Text (string) fields when using the graduated
symbolization option.

### Creating our first Choropleth

We will start our choropleth exercise by mapping the distribution of
poverty in Los Angeles County in census tracts.

73. Go back to the "Symbology" setting, by going to
    "**Properties**" \>\> "**Symbology**"

74. Click the dropdown where it says, "**Single Symbol**" and choose
    "**Graduated**":

    ![](./images//media/image81.png){width="5.898611111111111in"
    height="2.7359208223972002in"}

    ![](./images//media/image82.png){width="6.155153105861768in"
    height="2.9027777777777777in"}

75. Under "**Value**", click the dropdown arrow and choose
    "**POVERTYPOP**":

    ![](./images//media/image83.png){width="5.433724846894139in"
    height="4.055555555555555in"}

    ![](./images//media/image84.png){width="6.5in"
    height="2.5833333333333335in"}

76. Nothing has changed yet, so click on "**Classify**":

    ![](./images//media/image85.png){width="4.663053368328959in"
    height="2.736111111111111in"}

77. By clicking classify, we classified the numerical data based on the
    statistical mode shown here:

    ![](./images//media/image86.png){width="4.705108267716535in"
    height="2.770469160104987in"}

You can click on histogram to get a better sense of how the data looks
in order to choose a more appropriate classification mode, but for now
let's draw our attention to the number of classes, which is 5. With a
graduate color scheme, each class gets its own color and so, it is not
usually a good idea to go higher than 5.

78. Go to "**Classes**" near the right side:

    ![](./images//media/image87.png){width="6.084681758530183in"
    height="4.222222222222222in"}

79. My preference is to stick with 4, which draws more attention darker
    and lighter areas better.

    ![](./images//media/image88.png){width="3.875in"
    height="3.106275153105862in"}

80. Side note: you can change the color ramp, by clicking on it:

    ![](./images//media/image89.png){width="4.383487532808399in"
    height="3.513888888888889in"}

81. When editing the color ramp, you can choose the two colors that make
    up the ramp, and here is some basic advice in doing so:

    -   Stick with one primary color if you are showing data that
        doesn't have negative values, like poverty.

    -   Choose two different primary colors if what you are showing does
        have negative values, like population growth.

    -   The more classes you choose, the harder it will be to
        distinguish them from each other.

    -   Pay attention to color blindness! A good website to help with
        choose a color-blind friendly color scheme is:
        <https://gka.github.io/palettes/>

82. Click "**OK**" and our map should look like the following:

    ![](./images//media/image90.png){width="3.1423753280839897in"
    height="2.9583333333333335in"}

83. What happened? Our map now has more details about where poverty is
    concentrated in Los Angeles County.

To get a sense as to how drastic the statistical methods affect the map,
let's change the data to "equal interval" and see what happens:

Exercise \#3

Use the "equal Interval" classification method to map the data

The resulting map should look like the following:

![](./images//media/image91.png){width="3.0681200787401575in"
height="2.8884251968503936in"}

### Mapping Categorical Data

Now we will turn our attention to the **County\_Boundaries-shp** zip we
downloaded earlier!

84. Outside of QGIS, unzip the "**County\_Boundaries-shp**" file

85. Return to QGIS, and add the "**County\_Boundaries.shp**" as a vector
    layer to our project.

86. Your layers should look like the following:

    ![](./images//media/image92.png){width="2.044445538057743in"
    height="2.0277777777777777in"}

87. Drag "**County\_Boundaries**" below the "poverty layer" so that the
    larger counties do not cover all of our data.

    ![](./images//media/image93.png){width="2.555686789151356in"
    height="2.5348523622047243in"}

88. Right click on the "**County\_Boundaries**" layer to go to
    "**Properties**"

89. Click on "**Symbolize**" and this time, switch from "**Simple
    Fill**" to "**Categorized**"

    ![](./images//media/image94.png){width="6.612694663167104in"
    height="4.930555555555555in"}

90. Click "**Value**":

    ![](./images//media/image95.png){width="6.456944444444445in"
    height="2.5in"}

91. Choose the field "**Type**":

    ![](./images//media/image96.png){width="4.652777777777778in"
    height="2.486111111111111in"}

92. Click "**Classify**"

    ![](./images//media/image97.png){width="6.029990157480315in"
    height="2.861111111111111in"}

93. Notice how the colors are randomized:

    ![](./images//media/image98.png){width="5.602643263342082in"
    height="3.1041666666666665in"}

94. Click "**OK**" to apply the changes to the map and it should look
    like the following:

    ![](./images//media/image99.png){width="5.229166666666667in"
    height="4.762431102362204in"}

95. The purple is a bit jarring, let's quickly change the color by right
    clicking on it in the layers panel:

    ![](./images//media/image100.png){width="5.430555555555555in"
    height="3.4805883639545057in"}

96. The color wheel should show up:

    ![](./images//media/image101.png){width="1.9236111111111112in"
    height="3.902711067366579in"}

97. Congratulations! You've successfully completed a categorical map!

> Feel free to change the color for the "**Other County**" as well. When
> choosing colors, it is important to bear in mind that a map with no
> visual hierarchy will be hard to understand. Visual hierarchy is the
> concept that important things are easier to see than less important
> things. Take for example these two versions of the map we just made:

![](./images//media/image102.png){width="2.778781714785652in"
height="2.513888888888889in"}
![](./images//media/image103.png){width="2.7777777777777777in"
height="2.5129811898512684in"}

One example of poor visual hierarchy is when the background map has more
vibrance than the main focus of the map, such as the one on the left
side.

Final Exercise!!

The time has come to put our skills to the test and answer our initial
research question. Return to the "**poverty\_in\_los\_angeles\_county**"
layer and use the "**POVERTY\_RA**" field to see the ratio of poverty to
people in Los Angeles.

### Working with multiple layers:

If you like the map you currently have, you can duplicate the layer and
hide it while you work on another one, by right clicking on the layer
and choosing duplicate.

![](./images//media/image104.png){width="1.9995363079615047in"
height="2.6597222222222223in"}

The copied layer will automatically be hidden, so click the "eye" icon
to unhide it, the same functionality of hiding and unhiding works on all
map layers.

![](./images//media/image105.png){width="2.2708333333333335in"
height="3.0049660979877517in"}![](./images//media/image106.png){width="2.251337489063867in"
height="2.9791666666666665in"}

### Exercise Answer:

-   Filter "POVERTY\_RA" to be "Greater than or equal to" .25

-   Export those selected values

-   Symbolize the values using graduated color scheme and the
    "POVERTY\_RA" field.

If the field has been successfully changed, then we should be able to
see which areas in Los Angeles County have more than 25% of people
living under the Federal Poverty Line:

![](./images//media/image107.png){width="3.2432217847769027in"
height="3.1876640419947506in"}

Exporting a map
---------------

Now that you have a map you are proud of, the time has come to open up
the "Print Layout" which is the QGIS way of styling the map with text,
legends, and other cartographic goodness.

98. Go to the "**Toolbar**" \>\> "**Project**" \>\> "**New Print
    Layout**"

    ![](./images//media/image108.png){width="2.342716535433071in"
    height="3.5208333333333335in"}

99. Give a name for your layout in the new window, "**Los Angeles
    Poverty**"

    ![](./images//media/image109.png){width="2.729306649168854in"
    height="1.3334022309711286in"}

100. Another window will appear, and since we are mainly authoring a
    map, let's add that first by clicking the "Add Map" button on the
    right side:

    ![](./images//media/image110.png){width="6.5in"
    height="3.441666666666667in"}

101. Click and drag to add the map to the print layout:

    ![](./images//media/image111.png){width="6.5in"
    height="3.584722222222222in"}

102. Click the "Text" button to add some text that will serve as our
    title:

    ![](./images//media/image112.png){width="6.5in"
    height="3.629166666666667in"}

103. Click and drag to add it to our canvas:

    ![](./images//media/image113.png){width="6.5in"
    height="3.629166666666667in"}

104. Click on "Lorem ipsum":

    ![](./images//media/image114.png){width="6.5in"
    height="3.629166666666667in"}

105. Click on "Item Properties":

    ![](./images//media/image115.png){width="6.5in"
    height="3.629166666666667in"}

106. Change the text under "Main Properties"

    ![](./images//media/image116.png){width="6.013888888888889in"
    height="3.3577548118985128in"}

107. Our title will be, "**Areas in Los Angeles with 25% of the
    population living below the Federal Poverty Rate, 2018**"

108. Under "**Appearance**" scroll or click the arrow to change the font
    size:

    ![](./images//media/image117.png){width="6.5in"
    height="3.647222222222222in"}

109. Change the horizontal alignment to "center":

    ![](./images//media/image118.png){width="6.5in"
    height="3.647222222222222in"}

110. Click the "**Add Legend**" button on the left:

    ![](./images//media/image119.png){width="6.5in"
    height="3.6333333333333333in"}

111. Drag and to add a legend:

    ![](./images//media/image120.png){width="6.5in"
    height="3.629166666666667in"}

112. The legend should look like the following:

    ![](./images//media/image121.png){width="6.5in"
    height="3.647222222222222in"}

113. You can fine tune the legend by clicking on the "Item" and then
    going to "Item Properties"

    ![](./images//media/image122.png){width="6.5in"
    height="3.647222222222222in"}

114. Scroll down to the box and uncheck "**Auto update**" to get more
    control:

    ![](./images//media/image123.png){width="2.7708333333333335in"
    height="3.376388888888889in"}

115. Click on the layer name "**poverty\_in\_la\_county\_over\_25**" and
    rename it to: "**Census Tracts with more than 25% of living in
    poverty**"

    ![](./images//media/image124.png){width="3.5001793525809273in"
    height="2.5973556430446196in"}

116. With the legend complete, you are ready to export the map!

117. Click on "**Layout**" \>\> "**Export as Image**":

    ![](./images//media/image125.png){width="2.6602318460192476in"
    height="3.763888888888889in"}

118. Choose a location for your map and click save.

119. Close the layout editor and save your QGIS project by going to
    "**Project**" \>\> "**Save** **As..**"

    ![](./images//media/image126.png){width="5.997178477690289in"
    height="3.1805555555555554in"}

120. Congratulations! You have completed your first mapping project in
    QGIS!
