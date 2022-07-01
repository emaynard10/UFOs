# UFOs
## Overview of the analysis
The purpose of this analysis is to add user input to filter data on UFO sightings to whichever specific criteria the user enters in the input boxes. This user input could filter the search on date, city, state, country, or UFO shape. The analysis uses D3 to 'listen' to the event of the user inputting information into the Filter Search section and either pressing 'Enter' or clicking outside of the search box. The analysis connects an index.html file to an app.js to display the information on a clean and attractive website. Before the user enters any data filters, the Search Filter boxes contain placeholder values to show the user what format/type of input the program is looking for. The placeholder values are greyed out and once an input is typed it will appear black.

![Screen Shot 2022-06-24 at 10 44 50 AM](https://user-images.githubusercontent.com/99676466/175608124-35e330cd-b4ba-4e6f-8521-c6df1dc1e1fc.png)


### Tools:
Javascript, HTML/CSS, Bootstrap, D3

## Results
Opening the html file will take the user to a site that looks just like the image above. The five input boxes on the left is how the user can scroll through the data to narrow the search. Following the format shown in the box the user can enter a date within the dates in the data to see the UFO reportings on that date. Or the user can enter any of the other criteria. If the enrty in the box is not present in the data, the table will filter to blank results. After typing the input the user simply has to press 'Enter' on their keyboard or click out of the input box and the table will update.

* HTML: the html code is linked to the other files with <script> tags. In this way the data.js and app.js files are connected to the html file. The D3 library, which provides a lot of code to make the filtering work by adding interactive functionality, is the first <script> tag. 
~~~
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/4.11.0/d3.js"></script>
~~~
In the Filter Search section of the HTML file the various inputs are added with list tags(<li/>). The list tags are provided below; the important part is to make sure the id is listed exactly as it is in the data.
~~~
<div class="container-fluid">
        <div class="row">
            <div class="col-md-3">
                <form class="bg-dark">
                    <p>Filter Search</p>
                    <ul class="list-group bg-dark" >
                        <li class="list-group-item bg-dark">
                            <label for="date">Enter Date</label>
                            <input type="text" placeholder="1/10/2010" id="datetime" />
                        </li>
                        <li class="list-group-item bg-dark" >
                            <label for="city">Enter City</label>
                            <input type="text" placeholder="denver" id="city" />
                        </li>
                        <li class="list-group-item bg-dark">
                            <label for="state">Enter State</label>
                            <input type="text" placeholder="co" id="state">
                        </li>
                        <li class="list-group-item bg-dark">
                            <label for="country">Country</label>
                            <input type="text" placeholder="us" id="country">
                        </li>
                        <li class="list-group-item bg-dark">
                            <label for="shape">Shape</label>
                            <input type="text" placeholder="triangle" id="shape">
                        </li>
                    </ul>
                </form>
            </div>
~~~
* Javascript: The Javascript code uses a buildTable() function to create the table from the data. Then is uses two functions to create the filters. The first function is below the filters variable as function updateFilters(). The goal of the function is just this: to update the filters it checks for if the element is changed and rebuilds the table if they are. At the end of the function is a call to the next function which is the fitlerTable() function. This function loops throughthe filters and keeps the data that matches the filtered values. The following code is used to 'listen' for the click or the Enter after the user adds an input:
~~~
d3.selectAll("input").on("change", updateFilters);
~~~
The following image shows the filter applied in the 'city' box of 'fresno' and the single result in the table:
  
![Screen Shot 2022-06-24 at 11 25 30 AM](https://user-images.githubusercontent.com/99676466/175611799-dbc59bfb-29b1-4c6e-a404-b9b2d5fa8310.png)

## Summary

* A drawback is the user cannot compare two dates or enter two criteria to be filtered; if they wanted to see both lights and circles they would only be able to enter those inputs and view the tables separately. There is also not very much data as it only show dates in January, it would be better to draw conclusions about UFO sightings from a bigger dataset. Another drawback is it requires the user to enter the filter correctly, if they do not do so it will return a blank table. 
  
* With the format is the way it is currently, the user has to delete the filter to go back to a less filtered table. The code could add some filter clearing to be better for the user. Adding a clear filters button would help with useability. Additionally, the website could be updated so the user could do some comparisons, such as show two cities that are nearby in side by side tables. It would also benefit from being able to add two criteria into the search at once. 
