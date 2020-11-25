<script>
    import ProgressBar from "./ProgressBar.svelte"
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

</style>


<div bp="grid">
    <h2 bp="grid offset-5@md 4@md 12@sm">
        Seconds Left:
    </h2>
</div>
<ProgressBar/>

<button class="start">Start</button>