<script>
  	import { onMount } from 'svelte';
  	import { Connection, clusterApiUrl, PublicKey } from '@solana/web3.js';

	export let name = 'Solana';
  	let balance = null;

	onMount(async () => {
		const connection = new Connection(clusterApiUrl('devnet'));
		const publicKey = new PublicKey('8RgqwaJkQCH9KjrSmzfrZxEhGy4YcuiMUTv1j58BWygt');
		const fetchedBalance = await connection.getBalance(publicKey);
		balance = fetchedBalance / 1e9;
	});
</script>

<main>
	<h1>Balance de Solana</h1>
	<h2>{name}
	<p>{balance !== null ? `${balance} SOL` : 'Cargando...'}</p>
</main>
