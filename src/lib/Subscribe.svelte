<script lang="ts">
	import type {Readable} from 'svelte/store';
	import {derivedKeys} from './derivedKeys.js';

	type Stores = $$Generic<Record<string, unknown>>;

	type $$Props = Stores;
	type $$Slots = {
		default: {[K in keyof Stores]: Stores[K] extends Readable<infer V> ? V : never};
	};

	const values = derivedKeys($$restProps as Record<string, unknown>);
</script>

<slot {...$values} />
