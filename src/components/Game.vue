<script>
    export default {
        data() {
            return {
                playerScore: 0,
                computerScore: 0,
                rounds: 1,
                computerChoices: ["Rock", "Paper", "Scissors"],
                computerPickedChoice: "",
                Result: "",
                showComputerOption: false,
                playerRockSelected: false,
                playerPaperSelected: false,
                playerScissorsSelected: false,
                OptionDisabled: false,
                NextRoundBtn: false,
                RepeatRoundBtn: false,
                StartAgainBtn: false,
                roundScoreDisplay: true
            };
        },
        methods: {
            PlayerSelectsRock() {
                const randomComputerChoice = Math.floor(Math.random() * this.computerChoices.length);
                this.computerPickedChoice = this.computerChoices[randomComputerChoice]
                this.playerRockSelected = true,
                this.OptionDisabled = true,
                this.showComputerOption = true

                if (this.computerPickedChoice === "Rock") {
                    this.Result = "This is a draw, please play the same round again",
                    this.RepeatRoundBtn = true
                } else if (this.computerPickedChoice === "Paper") {
                    this.Result = "Computer has won this round",
                    this.NextRoundBtn = true,
                    this.computerScore++
                } else {
                    this.Result = "You as player has won this round",
                    this.NextRoundBtn = true,
                    this.playerScore++
                }
            },

            PlayerSelectsPaper() {
                const randomComputerChoice = Math.floor(Math.random() * this.computerChoices.length);
                this.computerPickedChoice = this.computerChoices[randomComputerChoice],
                this.playerPaperSelected = true,
                this.OptionDisabled = true,
                this.showComputerOption = true

                if (this.computerPickedChoice === "Paper") {
                    this.Result = "This is a draw, please play the same round again",
                    this.RepeatRoundBtn = true
                } else if (this.computerPickedChoice === "Scissors") {
                    this.Result = "Computer has won this round",
                    this.NextRoundBtn = true,
                    this.computerScore++
                } else {
                    this.Result = "You as player has won this round",
                    this.NextRoundBtn = true,
                    this.playerScore++
                }
            },

            PlayerSelectsScissors() {
                const randomComputerChoice = Math.floor(Math.random() * this.computerChoices.length);
                this.computerPickedChoice = this.computerChoices[randomComputerChoice],
                this.playerScissorsSelected = true,
                this.OptionDisabled = true,
                this.showComputerOption = true

                if (this.computerPickedChoice === "Scissors") {
                    this.Result = "This is a draw, please play the same round again",
                    this.RepeatRoundBtn = true
                } else if (this.computerPickedChoice === "Rock") {
                    this.Result = "Computer has won this round",
                    this.NextRoundBtn = true,
                    this.computerScore++
                } else {
                    this.Result = "You as player has won this round",
                    this.NextRoundBtn = true,
                    this.playerScore++
                }
            },

            NextRoundBtnClick() {
                this.Result = "",
                this.NextRoundBtn = false,
                this.rounds++,
                this.OptionDisabled = false,
                this.playerRockSelected = false,
                this.playerPaperSelected = false,
                this.playerScissorsSelected = false,
                this.showComputerOption = false

                if (this.rounds === 6) {
                    this.playerRockSelected = false,
                    this.playerPaperSelected = false,
                    this.playerScissorsSelected = false,
                    this.StartAgainBtn = true,
                    this.roundScoreDisplay = false,
                    this.OptionDisabled = true

                    if (this.playerScore > this.computerScore) {
                        this.Result = "You as the player has won the game"
                    } else {
                        this.Result = "The computer has won the game"
                    }
                }
            },

            RepeatRoundBtnClick() {
                this.Result = "",
                this.OptionDisabled = false,
                this.playerRockSelected = false,
                this.playerPaperSelected = false,
                this.playerScissorsSelected = false,
                this.showComputerOption = false,
                this.RepeatRoundBtn = false
            },

            StartAgainBtnClick() {
                window.location.reload();
            }
        }
    };
</script>



<template>

    <div>
        <div class="space-x-8">
            <button class="border-4 border-black py-1 px-2 text-3xl font-bold" v-on:click="PlayerSelectsRock" v-bind:class="{ 'bg-green-500': playerRockSelected }" v-bind:disabled="OptionDisabled">Rock</button>
            <button class="border-4 border-black py-1 px-2 text-3xl font-bold" v-on:click="PlayerSelectsPaper" v-bind:class="{ 'bg-green-500': playerPaperSelected }" v-bind:disabled="OptionDisabled">Paper</button>
            <button class="border-4 border-black py-1 px-2 text-3xl font-bold" v-on:click="PlayerSelectsScissors" v-bind:class="{ 'bg-green-500': playerScissorsSelected }" v-bind:disabled="OptionDisabled">Scissors</button>
        </div>
    </div>

    <div class="mt-6 space-y-2 font-bold text-2xl">
        <p v-show="roundScoreDisplay">Round: {{ rounds }} of 5</p>
        <p>Player Score: {{ playerScore }}</p>
        <p>Computer Score: {{ computerScore }}</p>

        <p v-show="showComputerOption">Computer Selects {{ computerPickedChoice }}</p>
        <p>{{ Result }}</p>

        <button v-show="NextRoundBtn" v-on:click="NextRoundBtnClick" class="border-4 border-black p-2">Next Round</button>
        <button v-show="RepeatRoundBtn" v-on:click="RepeatRoundBtnClick" class="border-4 border-black p-2">Repeat Round</button>
        <button v-show="StartAgainBtn" v-on:click="StartAgainBtnClick"  class="border-4 border-black p-2">Start Again</button>

    </div>

</template>