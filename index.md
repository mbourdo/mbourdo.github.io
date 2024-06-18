---
layout: default
title: Home
---

# Home

About me 

## Resume

Click the Education and Work Expirence tabs

## Projects

Click projects in the nav bar to view my latest projects

<!DOCTYPE html>
<html>
<head>
  <title>Google Charts with Google Sheets</title>
  <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
  <script type="text/javascript">
    // Load the Visualization API and the corechart package.
    google.charts.load('current', {'packages':['corechart']});

    // Set a callback to run when the Google Visualization API is loaded.
    google.charts.setOnLoadCallback(drawChart);

    function drawChart() {
      // Define the query to get data from Google Sheets
      var queryString = encodeURIComponent('SELECT A, B');

      // Create a query to fetch data from Google Sheets
      var query = new google.visualization.Query(
          'https://docs.google.com/spreadsheets/d/1QRRGK9xn1eGplvarZjEGhb7VpIGn2vNQCuuAkLimBOs/gviz/tq?sheet=Sheet1&tq=' + queryString);

      // Send the query with a callback function
      query.send(handleQueryResponse);
    }

    function handleQueryResponse(response) {
      if (response.isError()) {
        console.log('Error in query: ' + response.getMessage() + ' ' + response.getDetailedMessage());
        return;
      }

      var data = response.getDataTable();

      // Create the chart options
      var options = {
        title: 'My Horizontal Bar Chart',
        hAxis: {title: 'Value'},
        vAxis: {title: 'Category'},
        bars: 'horizontal'
      };

      // Instantiate and draw the chart
      var chart = new google.visualization.BarChart(document.getElementById('chart_div'));
      chart.draw(data, options);
    }
  </script>
</head>

<body>
  <div id="chart_div" style="width: 900px; height: 500px;"></div>
</body>
</html>
