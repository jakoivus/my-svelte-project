<script>
    import Title from './Title.svelte'


</script>

<section class='form'>
<div class='outer-container'>
    <div class='container'>
        <h1 >lisää lapsi</h1> 
        <form>
        <div class='row'>
            <div class='form-control'> 
                <label for="name">Nimi</label>
                <input type='text' id='name'>
            </div>
            
            <div class='form-control row-right'> 
                <label for="age">Ikä</label>
                <input type='text' id='age'>
            </div>
        </div>
        <p></p>
        <button type='submit' class='btn btn-block'>Lissää</button>
        </form>
    </div>
</div>
</section>