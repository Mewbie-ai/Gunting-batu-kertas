<!DOCTYPE html>
<head>
	<meta charset="UTF-8">
	<title>game</title>
</head>
<body>
	<button id = 'Rock'>Rock</button>
	<button id = 'Paper'>Paper</button>
	<button id = 'Scissors'>Scissors</button>

	<!-- Show result text -->
	<div id="result"></div>

	<!-- Show result scores -->
	<div>Player: <span id = 'pScore'>0</span></div>
	<div>Computer: <span id = 'cpScore'>0</span></div>

	<!-- Javascript -->
	<script>
		const buttons    = document.querySelectorAll('button');
		const result     = document.querySelector('#result');
		const pScoreDiv  = document.querySelector('#pScore');
		const cpScoreDiv = document.querySelector('#cpScore');

		let pScore  = 0;
		let cpScore = 0;


		buttons.forEach(button => {
			button.addEventListener('click', () => {
				if (pScore >= 5 || cpScore >= 5){
					return;
				}
				game(button);
			});
		});


		function computerPlay() {
			let x = Math.floor(Math.random() * 3);
			let result = ['Rock','Paper','Scissors'];
			console.log(x);
			return result[x];
		}

		/*If Player plays rock, computer return rock/paper/scissor
		If player wins return 'You win! x beats y'
		If computer wins return 'You lose! y beats x'
		If draw return 'Draw!' */
		function game(button) {
			const playerSelection = button.id;
			let computerSelection = computerPlay();

			function playRound(playerSelection, computerSelection) {
				console.log("Player selection: " + playerSelection + ", Computer Selection: " + computerSelection);
				var returnString = "";

				if (playerSelection != null) {
					if (playerSelection == 'Rock') {
						if (computerSelection == 'Scissors') {
							returnString = 'You win! rock beats scissors';
							pScore++;
						} else if (computerSelection == 'Paper') {
							returnString = 'You lose! paper beats rock';
							cpScore++;
						} else if (computerSelection == 'Rock') {
							returnString = 'Draw!';
						}
					} else if (playerSelection == 'Paper') {
						if (computerSelection == 'Scissors') {
							returnString = 'You lose! scissors cuts paper';
							cpScore++;
						} else if (computerSelection == 'Paper') {
							returnString = 'Draw!';
						} else if (computerSelection == 'Rock') {
							returnString = 'You win! paper beats rock';
							pScore++;
						}
					} else if (playerSelection == 'Scissors') {
						if (computerSelection == 'Scissors') {
							returnString = 'Draw!';
						} else if (computerSelection == 'Paper') {
							returnString = 'You win! scissors cuts paper';
							pScore++;
						} else if (computerSelection == 'Rock') {
							returnString = 'You lose! rock beats scissors';
							cpScore++;
						}
					}
				}
				result.innerText = returnString;
				pScoreDiv.innerText = pScore;
				cpScoreDiv.innerText = cpScore;
				return returnString;
			}
			return(playRound(playerSelection, computerSelection));
		}
		/* End function */
	</script>
</body>
</html>
