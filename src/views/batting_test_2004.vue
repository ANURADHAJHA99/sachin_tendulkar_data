<template>
    <div class="batting_test_2004">

        <div class="card center">
          <span class="title-imp">Important factors in Test format</span>
          <hr>
          <br>
          <span class="result-ps">1. <b>Conversion 50's into 100's</b> plays an important role in the
            Test cricket format since it is equally important to score big runs
          </span>
          <span class="result-ps">2. <b>Conversion 100's into 200's</b> plays an crucial role in
            Test cricket format since a double century will give you a powerful win
          </span>
          <span class="result-ps">3. <b>Number of 6's & 4's</b> provide runs faster
            compared to non-boundaries & hence are prefferable when you have to score big
          </span>
        </div>

        <el-tag class="tags bottomtags">
          <b>Consistency of Player:</b>
          Average runs, Runs at Home VS Away matches & ICC Ranking
        </el-tag>
        

        <div class="card">
            <Chart
            titleText="Avg Runs Scored (Home vs Away)"
            subTitleText="Let's see which player is durable under pressure"
            chartType="bar"
            :chartData="HomeAwayScoreData.data"
            :chartOptions="HomeAwayScoreData.options"
            :parentStyle="chartContainerStyle"
            />
            <Inference
            winner="Sir Don Bradman"
            titleText="scoring under pressure"
            />
            <br/>
            <el-popover
              placement="top-start"
              title="Home Score"
              width="200"
              trigger="hover"
              content="Score of a player when he scores in the country of his nationality">
              <el-button slot="reference">Define Home Score</el-button>
            </el-popover>
            <el-popover
              placement="top-start"
              title="Away Score"
              width="200"
              trigger="hover"
              content="Score of a player when he scores in the country in whose oppsition
                        he's playing">
              <el-button slot="reference">Define Away Score</el-button>
            </el-popover>
        </div>

        <el-tag class="tags bottomtags">
          <b>Player Dominance:</b>
          Conversion rate of 50s into 100s, 100s into 200s & Man of the Match Awards
        </el-tag>

        

        <el-tag class="tags bottomtags">
          <b>Hitting Strength:</b> Strike Rate, Number of Boundaries
        </el-tag>

        

    </div>
</template>

<script>
import Chart from '@/components/Chart.vue';
import Inference from '@/components/Inference.vue';
import PlayerDetailsCard from '@/components/PlayerDetailsCard.vue';

import batting_test_2004 from '../../json/batting_till_2004.json';

export default {
  name: 'batting_test_2004',
  components: {
    Chart,
    Inference,
    PlayerDetailsCard,
  },
  data() {
    return {
      chartContainerStyle: {
        margin: '10px',
        width: '45vw',
        display: 'inline-block',
      },
      
      HomeAwayScoreData: {
       HomeAwayScoreData: {
        options: {
          responsive: true,
        },
        data: {
          labels: [],
          datasets: [],
        },
      },
    },
    };
  },
     
 mounted(){
    const homeAwayScoreData = [];
    Object.values(batting_test_2004).forEach((player) => {
      homeAwayScoreData.push({
        name: player.year,
        awayAvg: player.info.batting_score,
       });
    });
    this.HomeAwayScoreData.data = {
      labels: homeAwayScoreData.map(t => t.name),
      datasets: [
        {
          label: 'Away',
          data: homeAwayScoreData.map(t => t.awayAvg),
          backgroundColor: [
          'rgb(255, 224, 230, 0.5)',
          'rgb(255, 226, 217, 0.5)',
          'rgb(255, 245, 221, 0.5)',
          'rgb(219, 242, 242, 0.5)',
          'rgb(215, 236, 251, 0.5)',
          'rgb(235, 224, 255, 0.5)',
          'rgb(244, 245, 245, 0.5)',
        ],
          borderWidth: 0.5,
          borderColor: [
          'rgb(255, 99, 132, 1)',
          'rgb(255, 159, 64, 1)',
          'rgb(255, 205, 86, 1)',
          'rgb(75, 192, 192, 1)',
          'rgb(54, 162, 235, 1)',
          'rgb(153, 102, 255, 1)',
          'rgb(201, 203, 207, 1)',
        ],
          hoverBorderWidth: 1,
          hoverBorderColor: [
          'rgb(255, 99, 132, 1)',
          'rgb(255, 159, 64, 1)',
          'rgb(255, 205, 86, 1)',
          'rgb(75, 192, 192, 1)',
          'rgb(54, 162, 235, 1)',
          'rgb(153, 102, 255, 1)',
          'rgb(201, 203, 207, 1)',
        ],
       
        
        }],
    };
 },
};

</script>

<style scoped>
.tags {
  margin-bottom: 20px;
  font-size: 16px;
}
.bottomtags {
  margin-top: 30px;
}
.center {
  text-align: center;
}
</style>
 