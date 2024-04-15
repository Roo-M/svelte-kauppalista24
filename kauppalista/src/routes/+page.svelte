<script>
    import {enhance} from "$app/forms";

    export let data;
    export let form;

</script>

<div class="komponentti">
    <h1>Kauppalista</h1>
    <ul>
        {#each data.asiat as asia}
            <li>
                <input type="checkbox">
                {asia}
            </li>
        {/each}
    </ul>
    {#if form?.error}
        <p class="error">{form.error}</p>
    {/if}
    <form class="uusi" method="POST" action="?/lisääAsia" use:enhance>
    <label for="uusi-asia">Lisää uusi asia:</label>
    <!-- svelte-ignore a11y-autofocus -->
    <input
        id="uusi-asia" 
        name="asia" 
        type="text"
        value={form?.asia ?? ""}
        required
        autofocus
    />
    <button>Lisää</button>

    </form>
</div>

<style>
    .komponentti {
        color: hwb(300 17% 71%);
        background-color: hwb(300 7% 47% / 0.5);
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        font-size: 20px;
    }
    h1 {
        font-size: 200%;
    }
    ul {
        font-size: 150%;
    }
    li {
        list-style-type: none;
    }
    .uusi {
    font-size: 125%;
    }
    label {
        display: block;
    }

</style>