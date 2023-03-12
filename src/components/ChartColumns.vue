<script setup lang="ts">
import { PropType } from 'vue';

const props = defineProps({
    data: { 
        type: Object as PropType<{
            day: string,
            amount: number,
            [key: string]: any
        }>, 
        required: true
    },
    isHighest: { type: Boolean },
    height: { type: Number, required: true }
})

</script>

<template>
    <div class="column">
        <div :id="isHighest? 'highest' : ''" class="col" :style="`height: ${height}%`">
            <label class="amount">${{ data.amount }}</label>
        </div>
        <label class="day"><small>{{ data.day }}</small></label>
    </div>
    
</template>

<style scoped>
.column {
    width: 10%; 
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: end;
}
    
    .col {
        position: relative;
        width: 100%;
        background-color: var(--soft-red);
        border-radius: 0.25rem;
    }
        
        .col:hover{
            cursor: pointer;
            background-color: var(--very-soft-red);
        }
            .col:hover .amount {
                visibility: visible;
            }
        .amount {
            position: absolute;
            top: 0;
            transform: translate(-0.8rem, -120%);
            visibility: hidden;
            padding: 0.5rem;
            border-radius: 0.5rem;
            background-color: black;
            color: var(--very-pale-orange);
            font-size: 0.8rem;
            font-weight: 700;
        }

    #highest {
        background-color: var(--cyan);
    }
        #highest:hover {
            background-color: var(--soft-cyan);
        }

    .day {
        color: var(--medium-brown);
    }
</style>
