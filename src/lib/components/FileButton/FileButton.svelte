<script lang="ts">
	/**
	 * Bind your file data for the file input.
	 * @type {FileList}
	 */
	export let files: FileList;
	/** Provide a button variant or other class styles. */
	export let button = 'variant-filled-secondary';

	let elemFileInput: HTMLElement;

	function onButtonClick(): void {
		elemFileInput.click();
	}

	function prunedRestProps(): any {
		delete $$restProps.class;
		return $$restProps;
	}
</script>

<div class="file-button {$$props.class ?? ''}" data-testid="file-button">
	<!-- Input: File -->
	<input bind:this={elemFileInput} bind:files type="file" {...prunedRestProps()} class="file-button-input hidden" on:change />
	<!-- Button -->
	<button
		class="file-button-btn btn {button}"
		type="button"
		disabled={$$restProps.disabled}
		on:click={onButtonClick}
		on:keydown
		on:keyup
		on:keypress
	>
		<slot />
	</button>
</div>
