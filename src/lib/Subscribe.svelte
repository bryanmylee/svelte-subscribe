<script lang="ts">
	import type { Readable } from 'svelte/store';
	import { derivedKeys } from '$lib/derivedKeys';

	type Stores = $$Generic<Record<string, unknown>>;

	type $$Props = Stores;
	type $$Slots = {
		default: { [K in keyof Stores]: Stores[K] extends Readable<infer V> ? V : never };
	};

	const values = derivedKeys($$restProps);
</script>

<slot {...$values} />
