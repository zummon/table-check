<script>
	let keys = $state([]);
	let array = $state();

	function handle(event) {
		let result = [];
		let value = event.target.value;
		value = value.split("\n");
		value = value.reduce((accu, str) => {
			accu.push(str.split("\t"));
			return accu;
		}, []);
		value.slice(1).forEach((row) => {
			let resultSec = {};
			value[0].forEach((key, index) => {
				resultSec[key] = row[index];
			});
			result.push(resultSec);
		});
		array = result;
	}
</script>

<div class="mx-auto flex max-w-3xl flex-wrap">
	<div class="w-full p-2">
		<textarea
			class="w-full resize-none text-black"
			rows="10"
			placeholder="paste .tsv text here"
			onchange={(event) => {
				handle(event);
			}}
		></textarea>
	</div>
	<div class="w-full p-2">
		<textarea
			class="w-full resize-none text-black"
			rows="10"
			placeholder="array of objects result"
			value={JSON.stringify(array)}
		></textarea>
	</div>
</div>
