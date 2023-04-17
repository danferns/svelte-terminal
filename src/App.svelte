<script>
    let prompt = "~/tech_urja >";

    const COMMANDS = {
        welcome: () => {
            return [
                "Welcome to this fictional terminal thing!",
                "For a list of commands, use `help`.",
            ];
        },
        help: () => {
            const commandList = Object.keys(COMMANDS);
            return ["Available Commands:", ...commandList.map((c) => `- ${c}`)];
        },
        clear: () => {
            output = [];
            return [];
        },
		links: () => {
			return ["Agnel Institue of Technology and Design",
                    "-Email: prinaitd@aitdgoa.edu.in",
                    "-Phone: 09975797916 / 919975797916",
                    "-Address: Agnel Technical Educational Complex, Assagao, Bardez – Goa 403507",
                    "Follow us on:-",
                    "-Instagram: https://instagram.com/aitdgoa?igshid=YmMyMTA2M2Y=",
                    "-Twitter: https://twitter.com/AitdGoa?t=j1EhwYYYxiFwNNlDYF4qCQ&s=09",
                    "-LinkedIn: https://www.linkedin.com/school/aitdgoa/"]
			
		},
        rick: () => {
			window.open("https://www.youtube.com/watch?v=dQw4w9WgXcQ")
		},
        credits: () => {
			return  ["Site Developed By", 
                     "-Ethan",
                     "-Daniel",
                     "-Valerian",
                     "-Warren",
                     "-Atreya"];
		}
    };

    let output = [];
    let input;

    function onKeyPress(e) {
        if (e.key === "Enter") {
            let text = input.value;
            input.value = "";
            output = [...output, prompt + " " + text];
            executeCommand(text);
        }
    }

    function executeCommand(text) {
        const args = text.trim().split(/\s/);
        const command = args[0];

        const result = getCommandResult(command, args);
        output = [...output, ...result];
    }

    function getCommandResult(command, args) {
        if (!Object.keys(COMMANDS).includes(command)) {
            return [
                `The command \`${command}\` does not exist.`,
                "Please check for typos or use `help` for the list of available commands.",
            ];
        }

        return COMMANDS[command](args);
    }

    executeCommand("welcome");
</script>

<div class="terminal" on:click={() => input.focus()} on:keydown={() => input.focus()}>
    {#each output as singleOutput}
        <div>
            {singleOutput}
        </div>
    {/each}

    {prompt}

    <input
        type="text"
        class="terminal-input"
        style:width="calc(100% - {prompt.length}ch - 24px)"
        bind:this={input}
        on:keypress={onKeyPress}
    />

    <br />
    <br />
</div>

<style>
    /* make the terminal fullscreen */
    :global(html, body) {
        height: 100%;
        width: 100%;
        padding: 0px;
        margin: 0px;
        overflow: hidden;
    }

    .terminal {
        height: calc(100% - 24px);
        overflow-y: auto;
        overflow-anchor: none;
    }

    /* styling */
    .terminal {
        padding: 12px;

        font-family: monospace;
        font-size: 18px;
        line-height: 2.5ch;

        color: #ef6e25;
        background: black;
    }

    .terminal-input {
        border: none;
        outline: none;
        background: inherit;
        color: inherit;
        font: inherit;

        padding: 0px;
    }
</style>
