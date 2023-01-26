<script>
    import {
        PUBLIC_OPENPUB_CONTRACT_ID,
        PUBLIC_OPENPUB_PUBLIC_KEY,
        PUBLIC_OPENPUB_ENS_DOMAIN,
    } from '$env/static/public'
    

    let items = [
        `Openpub contract: <a href="https://etherscan.io/tx/${PUBLIC_OPENPUB_CONTRACT_ID}" target="_blank" rel="noreferrer">${PUBLIC_OPENPUB_CONTRACT_ID}</a>`,
        `OpenPub owner public key:  <a href="https://etherscan.io/address/${PUBLIC_OPENPUB_PUBLIC_KEY}" target="_blank" rel="noreferrer">${PUBLIC_OPENPUB_PUBLIC_KEY}</a>`,
        `OpenPub ENS domain: <a href="https://etherscan.io/enslookup-search?search=openpub.eth" target="_blank" rel="noreferrer">${PUBLIC_OPENPUB_ENS_DOMAIN}</a>`,
    ]

</script>


<p>
    OpenPub is a decentralized protocol that runs on the Ethereum blockchain. Protocol details:
</p>
<ul>
    {#each items as item}
        <li>
            {@html item}
        </li>
    {/each}
</ul>


