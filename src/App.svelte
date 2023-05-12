<script>
	let keys = [];
	let array = [];
</script>

<div class="mx-auto flex max-w-3xl flex-wrap">
	<div class="w-full p-2">
		<textarea
			class="w-full resize-none text-black"
			rows="10"
			on:change={(event) => {
				let result = [];
				let value = event.target.value;
				value = value.split("\n");
				value = value.reduce((accu, str) => {
					accu.push(str.split("	"));
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
			}}
		/>
	</div>
	<div class="w-full p-2">
		<textarea
			class="w-full resize-none text-black"
			rows="10"
			value={JSON.stringify(array)}
		/>
	</div>
</div>
