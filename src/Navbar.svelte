<script>
    //
    function handleClick() {
        window.alert("Lisää painettu")
    }   
</script>

<style>

</style>

<nav>
    <div class="nav">
        <div class="nav-center">
            <h1 class="nav-title">NavBar</h1>
            <button type='button' class='nav-btn' on:click={handleClick}><i class="fa fa-plus-square" />LISÄÄ</button>
        </div>
    </div>
</nav>