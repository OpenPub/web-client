<script>
    export let pub = {
        title: "",
        authors: [""],
        description: "",
    }
    export let pubIsValid = false

    /**
	 * @param {number} idx
	 */
    function removeAuthor(idx) {
        pub.authors = pub.authors.filter((x, i) => idx !== i)
    }

    function addAuthor() {
        pub.authors = [...pub.authors, ""]
    }

    function submit() {
        console.log(pub)
    }


    /**
	 * @param {{ title: any; authors?: string[]; description?: string; }} pub
	 */
    function checkValidity(pub) {
        if (pub.title.length) {
            pubIsValid = true
        } else {
            pubIsValid = false
        }
    }

    $: checkValidity(pub)
    
</script>

<h1>Publish</h1>

<input class="form-control" type="text" placeholder="Title" bind:value={pub.title} />

<textarea class="form-control mt-3" rows="5" placeholder="Description" bind:value={pub.description}></textarea>

<div class="my-3">
    <div class="d-flex">

        <div class="me-2">
            <button class="btn btn-primary text-nowrap" type="button" on:click={addAuthor}>
                <i class='bi bi-plus-lg me-2'></i>Author
            </button>            
        </div>

        <div class="w-100">
            {#each pub.authors as author, author_idx}
                <div class="input-group mb-2 w-100">
                    <input class="form-control" type="text" placeholder="Author name" bind:value={pub.authors[author_idx]} />
                    {#if author_idx }
                        <button type="button" class="btn btn-outline-secondary" on:click={() => {removeAuthor(author_idx)}}>
                            <i class='bi bi-x-lg'></i>
                        </button>
                    {/if}
                </div>
            {/each}   
        </div>

    </div>
</div>
<div>
    <button
        type="button"
        class="btn btn-success"
        disabled="{!pubIsValid}"
        on:click={submit}>
        <i class='bi bi-lock me-2'></i>
    </button>
</div>
