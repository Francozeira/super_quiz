<template>
    <div class="result" :class="{wrong: !result}">
        <span v-if="result">Well done =D, nailed it!</span>
        <span v-else>Nope, not this time :(</span>
        <button @click="$emit('confirmed')" autofocus type="button">Next one</button>
    </div>
</template>

<script>

export default {
	props: {
		result: {
			type: Boolean,
			required: true
		}
	},
}
</script>

<style>
	.result {
		height: 300px;
		color: #000;
		background-color: #FFF;
		width: 70%;
		border-radius: 20px;
		font-size: 5.5rem;
		display: flex;
		flex-direction: column;
		justify-content: center;
		background-color: #89c454;
		color: #30863d;
	}

	.result hr {
		color: #FFF;
	}

	.result.wrong {
		background-color: #f05250;
		color: #bb2814;
	}

	.result button {
		outline: none;
		align-self: center;
		padding: 10px 20px;
		font-size: 1.7rem;
		border-radius: 8px;
		background-color: #FFF;
		color: #30863d;
		font-weight: 600;
		font-family: 'Alegreya', serif;
		margin: 30px 0
	} 

	.result button {
		color: #89c454;
	}

	.result.wrong button {
		color: #f05250;
	}

	.result button:hover {
		cursor: pointer;
		background-color: rgb(238, 238, 238);
		color: #30863d;

	}
	.result.wrong button:hover {
		cursor: pointer;
		background-color: rgb(238, 238, 238);
		color: #bb2814;

	}
</style>
