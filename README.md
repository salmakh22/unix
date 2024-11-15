# unix
# guessinggame.sh

#!/bin/bash

# Function to get the number of files in the current directory
function count_files {
    echo $(ls -1 | wc -l)
}

file_count=$(count_files)
user_guess=-1

echo "Welcome to the Guessing Game!"
echo "Can you guess how many files are in the current directory?"

# Loop until the correct guess
while [[ $user_guess -ne $file_count ]]; do
    read -p "Enter your guess: " user_guess

    if [[ $user_guess -lt $file_count ]]; then
        echo "Your guess is too low. Try again!"
    elif [[ $user_guess -gt $file_count ]]; then
        echo "Your guess is too high. Try again!"
    else
        echo "Congratulations! You guessed correctly!"
    fi
done

# makefile

README.md: guessinggame.sh
	echo "# Guessing Game Project" > README.md
	echo "## Description" >> README.md
	echo "This project is a Bash script guessing game." >> README.md
	echo "## Date and Time" >> README.md
	echo "$(shell date)" >> README.md
	echo "## Number of Lines in guessinggame.sh" >> README.md
	echo "$(shell wc -l < guessinggame.sh)" >> README.md
