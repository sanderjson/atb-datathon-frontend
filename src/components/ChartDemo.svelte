 <script>
  import { onMount } from "svelte";
  import Chart from 'chart.js';
  import axios from 'axios';

  function createChart() {
    var ctx = document.getElementById("myChart");
    
    axios({
      method: "put",
      url: "http://18.220.251.195/api/user",
      responseType: "json"
    })
      .then(function (response) {
        
      });
    var myChart = new Chart(ctx, {
      type: "pie",
      data: {
        labels: [""],
        datasets: [
          {
            label: "# of Votes",
            data: [12, 19, 3, 5],
            backgroundColor: [
              "rgba(255, 99, 132, 0.2)",
              "rgba(54, 162, 235, 0.2)",
              "rgba(255, 206, 86, 0.2)",
              "rgba(75, 192, 192, 0.2)",
              "rgba(153, 102, 255, 0.2)",
              "rgba(255, 159, 64, 0.2)"
            ],
            borderColor: [
              "rgba(255, 99, 132, 1)",
              "rgba(54, 162, 235, 1)",
              "rgba(255, 206, 86, 1)",
              "rgba(75, 192, 192, 1)",
              "rgba(153, 102, 255, 1)",
              "rgba(255, 159, 64, 1)"
            ],
            borderWidth: 1
          }
        ]
      },
      options: {
        scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true
              }
            }
          ]
        }
      },
      options: {
        responsive: true,
        title: {
          fontSize: 20,
          fontColor: '#000000',
          display: true,
          text: "Your Accounts",
        },
        legend: {
          align: 'end'
        }
      }
    });

    var balanceChartCanvas = document.getElementById("balanceChart");
    var balanceChart = new Chart(balanceChartCanvas, {
      type: "line",
      data: {
        
        labels: ["Nov", "Dec", "Jan", "Feb"],
        datasets: [{
          borderColor: 'rgba(98, 190, 193)',
          pointBackgroundColor: 'rgba(255,255,255)',
          fill: false,
          label: "Time",
          data:[ 1000, 1520, 500, 30]}
        ]
      },
      options: {
        legend: {
          display: false
        },
        responsive: true,
        title: {
          fontSize: 20,
          fontColor: '#000000',
          display: true,
          text: "Your Accounts Activity",
        },
        scales: {
            xAxes: [{
              gridLines: {
              },
              display: false
            }],
            yAxes: [{
              gridLines: {
                show: false
              }
            }]
          }
      }
    })
  }

  onMount(createChart);
</script>

<div id="dashboard">
  <div className="chartContainer">
      <canvas id="balanceChart"/>
    </div>
  <div className="relative m-auto max-w-12" >
    <canvas id="myChart" width="600" height="400"/>
  </div>
</div>

