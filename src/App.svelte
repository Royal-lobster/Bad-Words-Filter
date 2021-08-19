<script>
import TextArea from "./TextAreaAutosize.svelte";
let message;
let output = "Enter text at top";
var handleSubmit = async (e) => {
    if (message ?.trim().length != 0) {
        console.log("Clicked submit")
        let url = `https://royalobster.npkn.net/bad-words-filter/?msg=${message.split(' ').join('%20')}`
        console.log(url)
        let res = await fetch(url);
        output = await res.text()
        console.log()
    }
}
</script>
<main>
	<section>
		<h1 class="title">Bad words filter</h1>
		<div class="inputs_container">
			<h1>
				Enter a Message here:
			</h1>
			<form class = "inputs">
				<TextArea type="text" bind:value={message}  minRows={1} maxRows={40}/>
				<button on:click|preventDefault={handleSubmit}>
					Censor the Text
				</button>
			</form>
		</div>

		<h1>
			Filtered Text:
		</h1>
		<p>
			{output}
		</p>
	</section>
	<footer>
		Made by Srujan with Svelte
	</footer>
</main>

<style>
    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
:global(body) {
    background-color: #e64c6d;
    position: relative;
    margin: 0;
    padding: 0;
}

.title{
	font-size: 50px;
	text-align: center;
	color: #dbd96e;
    margin-bottom: 30px;
}
main {
    display: grid;
    place-items: center;
    min-height: 100vh;
    padding: 10px;
}
.inputs_container{
	background-color: #ffffff34;
    padding: 10px;

}
section h1 {
    font-family: helvetica;
    font-weight: 900;
    color: #6b0935;
    margin: 10px 0;
}

.inputs {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

button {
    display: inline-block;
    cursor: pointer;
    padding: .7em 1.4em;
    border-radius: .15em;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    text-decoration: none;
    text-transform: uppercase;
    font-weight: 900;
    color: #2a4f1d;
    background-color: #75e84f;
    -webkit-box-shadow: inset 0 -0.6em 0 -0.35em rgb(0 0 0 / 17%);
    box-shadow: inset 0 -0.6em 0 -0.35em rgb(0 0 0 / 17%);
    text-align: center;
}

p {
    white-space: pre-wrap;
    text-align: left;
    max-width: 450px;
    display: block;
    font: normal 20px/30px Monaco, Monospace !important;
    color: #CFDBEC;
    background-color: #2f2f2f;
    padding: 0 1em;
    margin: 0;
    overflow: auto;
}

footer {
    background: #326fa8;
    color: white;
    padding: 5px 0;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    width: 100vw;
    text-align: center;
}
@media only screen and (max-width: 500px) {
    p {
        max-width: 95vw;
    }
}
</style>
