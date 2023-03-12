<script setup lang="ts">
import data from '../data.json'
import ChartColumns from '../components/ChartColumns.vue';

const columns = [...data];
const highest = findMax();

function findMax() {
    let max = columns[0].amount;
    for (let i = 1; i < columns.length; i++) {
        if (max < columns[i].amount) max = columns[i].amount;
    }

    return max;
}

</script>

<template>
    <div class="balance">
        <div>
            <label for="myBalance"><small>My balance</small></label>
            <h2 id="myBalance">$921.48</h2>
        </div>
        <img src="../assets/logo.svg" alt="Logo">
    </div>
    <div class="statistic">
        <div class="chart">
            <h2>Spending - Last 7 days</h2>
            <div class="chartColumns">
                <ChartColumns :is-highest="column.amount === highest ? true : false" :data="column" v-for="column in columns" :height="column.amount / highest * 100"></ChartColumns>
            </div>
        </div>
        <div class="expenses">
            <label for="monthExpenses"><small>Total this month</small></label>
            <div class="numbers">
                <h1 id="monthExpenses">$478.33</h1>
                <div class="comparision">
                    <h6 id="compareNum">+2.4%</h6>
                    <label for="compareNum"><small>from last month</small></label>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.balance {
    background-color: var(--soft-red);
    padding: 1.5rem;
    border-radius: 1rem;
    display: flex;
    justify-content: space-between;
    color: var(--very-pale-orange);
    margin-block-end: 1rem;
}
    .balance h2 {
        margin-block: 0;
    }
    .balance label {
        font-weight: 400;
    }

.statistic {
    background-color: var(--very-pale-orange);
    padding: 1.5rem;
    border-radius: 1rem;
}
    .chart {
        border-block-end-style: solid;
        border-block-end-width: 0.05rem;
        border-block-end-color: var(--very-soft-red);
    }
        .chart h2{
            margin-block-start: 0;
            color: var(--dark-brown);
        }
        .chartColumns {
            margin-block-start: 2rem;
            margin-block-end: 1rem;
            display: flex;
            justify-content: space-between;
            height: 10rem;
        }
    
    .expenses {
        margin-block-start: 1rem;
        color: var(--dark-brown);
    }
        .expenses h1 {
            margin-block: 0;
        }
        .numbers {
            display: flex;
            justify-content: space-between;
            text-align: end;
        }
            .comparision h6{
                margin-block: 0;
                text-align: end;
            }
        .expenses label {
            color: var(--medium-brown);
            font-weight: 400;
        }
</style>