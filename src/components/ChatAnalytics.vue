<template>
  <div>
    <div class="grid grid-cols-2 gap-4 mb-4">
      <div class="bg-blue-50 p-3 rounded-lg">
        <div class="text-sm text-gray-500">Total Questions</div>
        <div class="text-xl font-semibold">{{ analytics.totalQuestions }}</div>
      </div>
      <div class="bg-green-50 p-3 rounded-lg">
        <div class="text-sm text-gray-500">Answered</div>
        <div class="text-xl font-semibold">{{ analytics.answeredQuestions }}</div>
      </div>
      <div class="bg-yellow-50 p-3 rounded-lg">
        <div class="text-sm text-gray-500">Success Rate</div>
        <div class="text-xl font-semibold">{{ successRate }}%</div>
      </div>
      <div class="bg-red-50 p-3 rounded-lg">
        <div class="text-sm text-gray-500">Fallbacks</div>
        <div class="text-xl font-semibold">{{ analytics.fallbackResponses }}</div>
      </div>
    </div>
    
    <div class="mb-4">
      <h3 class="text-sm font-medium text-gray-500 mb-2">Daily Interactions</h3>
      <div class="h-32">
        <BarChart :chart-data="chartData" :options="chartOptions" />
      </div>
    </div>
    
    <div>
      <h3 class="text-sm font-medium text-gray-500 mb-2">Top Questions</h3>
      <ul class="text-sm">
        <li v-for="(item, index) in analytics.topQuestions" :key="index" class="flex justify-between py-1">
          <span class="truncate mr-2">{{ item.question }}</span>
          <span class="text-gray-500">{{ item.count }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { computed, ref, watch } from 'vue';
import { Bar as BarChart } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

export default {
  name: 'ChatAnalytics',
  components: {
    BarChart
  },
  props: {
    analytics: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    // Calculate success rate
    const successRate = computed(() => {
      if (props.analytics.totalQuestions === 0) return 0;
      return Math.round((props.analytics.answeredQuestions / props.analytics.totalQuestions) * 100);
    });

    // Prepare chart data
    const chartData = computed(() => {
      const labels = props.analytics.dailyInteractions.slice(-7).map(item => {
        const parts = item.date.split('-');
        return `${parts[1]}/${parts[2]}`; // MM/DD format
      });
      
      const data = props.analytics.dailyInteractions.slice(-7).map(item => item.count);
      
      return {
        labels,
        datasets: [
          {
            label: 'Interactions',
            backgroundColor: '#3B82F6',
            data
          }
        ]
      };
    });

    // Chart options
    const chartOptions = {
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        legend: {
          display: false
        }
      },
      scales: {
        y: {
          beginAtZero: true,
          ticks: {
            precision: 0
          }
        }
      }
    };

    return {
      successRate,
      chartData,
      chartOptions
    };
  }
};
</script>