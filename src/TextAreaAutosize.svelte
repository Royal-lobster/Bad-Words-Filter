<script>
export let value = '';
export let minRows = 1;
export let maxRows;

$: minHeight = `${1 + minRows * 1.2}em`;
$: maxHeight = maxRows ? `${1 + maxRows * 1.2}em` : `auto`;
</script>

<div class="container">
    <pre
        aria-hidden="true"
        style="min-height: {minHeight}; max-height: {maxHeight};"
        class="text-area-pre"
        >{value + '\n'}</pre>

    <textarea bind:value></textarea>
</div>

<style>
.container {
    position: relative;
}

pre,
textarea {
    font-family: inherit;
    padding: 0.5em;
    box-sizing: border-box;
    border: 1px solid #eee;
    line-height: 1.2;
    overflow: hidden;
}

textarea {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    resize: none;
}

textarea:focus {
    outline: none;
    box-shadow:
        0 0px 2.7px rgba(0, 0, 0, 0.022),
        0 0px 6.9px rgba(0, 0, 0, 0.031),
        0 0px 14.2px rgba(0, 0, 0, 0.039),
        0 0px 29.2px rgba(0, 0, 0, 0.048),
        0 0px 80px rgba(0, 0, 0, 0.07);
}

.text-area-pre {
    max-width: 400px
}

@media only screen and (max-width: 500px) {
    .text-area-pre {
        max-width: 80vw;
    }
}
</style>
