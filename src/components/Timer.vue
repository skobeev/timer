<template>
    <div class="timer" v-bind:class="{active: timer.run}">

        <span class="time">
            {{ `${timer.hour}:${timer.minute}:${timer.sec}` }}
        </span>

        <hr v-bind:class="{active: timer.run}">

        <div class="play" v-bind:class="{off: timer.run}">
            <button v-on:click="timer.run=!timer.run">
            </button>
        </div>

        <div class="stop" v-bind:class="{active: timer.run}">
            <button v-on:click="timer.run=false, 
                                timer.sec=0,
                                timer.minute=0,
                                timer.hour=0">
            </button>
        </div>
    </div>
</template>

<script>
    export default{
        props: ['timer','id'],
    }
</script>

<style>
    .timer.active{
        color: white;
    }
    .stop.active, hr.active{
        background: white;
    }
    .timer{
        color: #9E9E9E;
        display: block;
        position: relative;
        width: 225px;
        height: 120px;
        background-color: #696969;
        margin-right: 25px;
        margin-left: 25px;
        margin-top: 25px;
        margin-bottom: 25px;
    }
    .timer hr{
        position: absolute;
        top: 50%;
        width: 100%;
        height: 1px;
        background: #9E9E9E;
        border: none;
    }

    span.time {
        display: block;
        text-align: center;
        margin-top: 25px;
        
    }
    .play, .stop{
        margin-top: 37px;
        width: 20px;
        height: 20px;
        background: #9E9E9E;
        float: left;
        
    }
    .play{
        position: absolute;
        left: 70px;
        clip-path: polygon(100% 50%, 0 100%, 0 0);
    }
    .play.off{
        box-sizing: content-box;
        width: 4px;
        border-right: 3px solid white;
        border-left: 3px solid white;
        clip-path: none;
        background: none;
    }
    .stop{
        position: absolute;
        right: 70px;
    }
    button{
        width: 12px;
        height: 100%;
        border: none;
        outline: none;
        background: none;
    }
    
</style>