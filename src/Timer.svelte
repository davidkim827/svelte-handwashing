<script>
    import { createEventDispatcher } from "svelte";
    import ProgressBar from "./ProgressBar.svelte";
    const totalSeconds = 20;
    let secondsLeft = totalSeconds;
    let isRunning = false;
    $: progress = (totalSeconds - secondsLeft) / totalSeconds * 100
    const dispatch = createEventDispatcher();

    function startTimer(){
        const timer = setInterval(() => {
        isRunning = true;
        secondsLeft -= 1;
        if (secondsLeft == 0){
            clearInterval(timer);
            isRunning = false;
            secondsLeft = totalSeconds;
            dispatch("end")
        }
    }, 1000);

    }

</script>

<style>
    h2 {
        margin:0;
    }
    .start {
        background-color: rgb(123, 333, 73);
        width: 100%;
        margin: 10px 0;
    }
    .start[disabled]{
        background-color: solid rgb(194, 194, 194);
        cursor: not-allowed;

    }

</style>


<div bp="grid">
    <h2 bp="grid offset-5@md 4@md 12@sm">
        Seconds Left: {secondsLeft}
    </h2>
</div>

<div bp="grid">
    <button disabled={isRunning} bp="grid offset-5@md 4@md 12@sm" class="start" on:click={startTimer}>Start</button>
</div>

<ProgressBar progress={progress}/>

