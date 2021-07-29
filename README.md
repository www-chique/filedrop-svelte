# FileDrop

A file dropzone action & component for [Svelte](https://svelte.dev/).

## Install

```bash
npm i filedrop-svelte -D

# yarn add filedrop-svelte -dev
```

## Usage

dropfile comes with both a component and an action. The component is basically a wrapper around the action with some very minimal styling as an example.

### Component

```html
<script>
	import FileDrop from "filedrop-svelte";
	import type { Files } from "filedrop-svelte";
	import fileSize from "filesize";
	let files: Files;
</script>

<FileDrop on:filedrop={(e) => { files = e.detail.files }}>
        Upload files
</FileDrop>

{#if files}
	<h3>Accepted files</h3>
	<ul>
		{#each files.accepted as file}
			<li>{file.name} - {fileSize(file.size)}</li>
		{/each}
	</ul>
	<h3>Rejected files</h3>
	<ul>
		{#each files.rejected as rejected}
			<li>{rejected.file.name} - {rejected.error.message}</li>
		{/each}
	</ul>
{/if}
```

### Action

```html
<script>
	import { filedrop } from "filedrop-svelte";
	import type { Files, FileDropOptions } from "filedrop-svelte";
	let options: FileDropOptions = {};
	let files: Files;
</script>

<div use:filedrop={options} on:filedrop={(e) => {files = e.detail.files}}>
	<!-- you can add your input[type="file"] here if you want.
	or you can omit it and it'll be appended -->
	Drag &amp; drop files
</div>
```

## References

### Previous art

- [svelte-file-dropzone](https://github.com/thecodejack/svelte-file-dropzone).

### Alternatives

- [svelte-file-dropzone](https://github.com/thecodejack/svelte-file-dropzone)

### Dependencies

- [attr-accept](https://github.com/react-dropzone/attr-accept)
- [file-selector](https://github.com/react-dropzone/file-selector)
- [filesize](https://github.com/avoidwork/filesize.js)
- [ua-parser-js](https://github.com/faisalman/ua-parser-js)
- [playwright](https://playwright.dev/)

## Todo

- tests
- better documentation
- demo website
