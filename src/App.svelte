<script>
    let prompt = "~/tech_urja >";

	const SPACE_FACTS = ["The Milky Way galaxy is estimated to contain over 100 billion planets.",
                         "The largest asteroid in our solar system is Ceres, which is located in the asteroid belt between Mars and Jupiter.",
                         "The International Space Station (ISS) travels at a speed of approximately 28,000 kilometers per hour (17,500 miles per hour).",
                         "A day on Venus is longer than a year on Venus, as it takes the planet 243 Earth days to complete one rotation on its axis, but only 225 Earth days to orbit the sun.",
                         "The first artificial satellite, Sputnik 1, was launched into space by the Soviet Union on October 4, 1957.",
                         "The tallest mountain in our solar system is Olympus Mons on Mars, which stands at a height of 22 kilometers (14 miles).",
                         "The Apollo 11 mission was the first time humans set foot on the moon, on July 20, 1969.",
                         "The Hubble Space Telescope is capable of capturing images of galaxies billions of light years away.",
                         "There are more than 170 known moons in our solar system.",
                         "The Kuiper Belt is a region of the solar system beyond the orbit of Neptune that contains many small, icy objects.",
                         "The sun makes up 99.86% of the total mass of our solar system.",
                         "The Great Red Spot on Jupiter is a massive storm that has been raging for at least 350 years.",
                         "The asteroid that is thought to have caused the extinction of the dinosaurs was approximately 10 to 15 kilometers (6 to 9 miles) in diameter.",
                         "The closest star to our solar system is Proxima Centauri, which is approximately 4.24 light years away.",
                         "The Kuiper Belt is home to dwarf planets such as Pluto, Haumea, and Makemake.",
                         "The largest volcano in our solar system is Olympus Mons on Mars, which is approximately 3 times taller than Mount Everest.",
                         "A year on Neptune is almost 165 Earth years long.",
                         "The temperature on the surface of Mercury can reach up to 430 degrees Celsius (806 degrees Fahrenheit) during the day.",
                         "The total mass of all the planets in our solar system combined is only about 0.14% of the mass of the sun.",
                         "The Cassini spacecraft discovered six new moons orbiting Saturn in 2004.",
                         "The first woman to travel to space was Valentina Tereshkova, who flew on the Vostok 6 mission launched by the Soviet Union in 1963.",
                         "The space between galaxies is not empty, but rather contains a thin gas known as the intergalactic medium.",
                         "The largest moon in our solar system is Ganymede, which is larger than the planet Mercury.",
                         "The Kuiper Belt is believed to be the source of many comets in our solar system.",
                         "A year on Uranus is approximately 84 Earth years long.",
                         "The distance between the sun and the Earth is approximately 149.6 million kilometers (93 million miles).",
                         "The largest canyon in our solar system is Valles Marineris on Mars, which is over 4,000 kilometers (2,500 miles) long.",
                         "The first American to travel to space was Alan Shepard, who flew on the Freedom 7 mission launched by NASA in 1961.",
                         "The temperature on the surface of Venus is hot enough to melt lead, reaching up to 462 degrees Celsius (864 degrees Fahrenheit).",
                         "The asteroid belt is a region between the orbits of Mars and Jupiter that contains numerous small, rocky objects.",
                         "The universe is around 13.8 billion years old.",
                         "The largest known star, UY Scuti, has a diameter of around 1,700 times that of our sun.",
                         "There are more stars in the universe than there are grains of sand on Earth.",
                         "A day on Venus is longer than a year on Venus.",
                         "The highest mountain in our solar system is Olympus Mons on Mars, which is three times higher than Mount Everest.",
                         "The Voyager 1 spacecraft, launched in 1977, is the farthest human-made object from Earth and has entered interstellar space.",
                         "If two pieces of the same type of metal touch in space, they will bond and become permanently stuck together.",
                         "The shortest day in the solar system is on Jupiter, which spins once on its axis every 9 hours and 56 minutes.",
                         "The sun makes up 99.86% of the total mass of our solar system.",
                         "The distance between the Earth and the sun is about 93 million miles (150 million kilometers).",
                         "Saturn's rings are made up of chunks of ice and rock, ranging in size from tiny grains to large mountains.",
                         "The first living beings sent into space were fruit flies, aboard a U.S. launched V-2 rocket in 1947.",
                         "The first human to orbit Earth was Yuri Gagarin, a Russian cosmonaut, on April 12, 1961.",
                         "There are more than 200 moons in our solar system.",
                         "The Milky Way galaxy contains at least 100 billion planets.",
                         "If you could travel at the speed of light, you could circle the Earth's equator 7.5 times in just one second.",
                         "There is a black hole at the center of our galaxy, the Milky Way.",
                         "The largest asteroid in our solar system, Ceres, is also a dwarf planet.",
                         "A neutron star is so dense that a single teaspoon of it would weigh about 6 billion tons.",
                         "The universe is expanding, and its expansion is accelerating."]

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
		},
        whereto: () => {
			window.open("https://goo.gl/maps/KdU82hjc5bjR1zQi6");
		},
        facts: () => {
			return [SPACE_FACTS[Math.floor(Math.random() * 50)]];
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
