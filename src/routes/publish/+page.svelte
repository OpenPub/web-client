<script>

    let title = ""
    let authors = ["", "d", "e", "f"]
    let description = ""

    $: authors;


    /**
	 * @param {number} idx
	 */
    function removeAuthor(idx) {
        authors.splice(idx, 1)
        console.log(authors)
    }

    function addAuthor() {
        authors.push("")
        console.log(authors)
    }



</script>

<h1>Publish</h1>

<input class="form-control" type="text" placeholder="Title" bind:value={title} />

<textarea class="form-control mt-3" rows="5" placeholder="Description" bind:value={description}></textarea>

<div class="mt-3">
    {#each authors as author, author_idx}

        <div class="input-group mb-2">

            <input class="form-control" type="text" placeholder="Author name" bind:value={authors[author_idx]} />

            {#if author_idx }
                <button type="button" class="btn btn-outline-secondary" on:click={() => {removeAuthor(author_idx)}}>
                    <i class='bi bi-x-lg'></i>
                </button>
            {/if}

        </div>

    {/each}   
    <button class="btn btn-primary" type="button" on:click={addAuthor}>
        Add author
    </button>
</div>
