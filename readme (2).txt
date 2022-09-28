import random
# Initial steps to start hangman game
# Importing Hangman parts from text file
hang=hang[]
with open('h2/hang.txt','r') as file:  
    # reading each line    
    for i,line in enumerate(file):
        hang.append(line)
# Importing words from text file
def words():
with open("h2/words.txt", "r") as f:
    for i in f:
        list=i.split(',')
word = random.choice(list).lower()
# Printing word for testing
print(word)
# Initializing parameters
guessed_correctly = []
guessed_incorrectly = []
def main():
tries = 5
count = -1
# Initializing while loop 
while tries > 0:
    output = ''
    for letter in word:
        if letter in guessed_correctly:
            output += letter
        else:
            output += '_ '
    if output == word:
        break
    print("Guess the word: ",output)
    # Printing the guessed word and chances left
    print(tries," chances left")
    guessed_word = input().lower()
    if guessed_word in guessed_correctly or guessed_word in guessed_incorrectly:
        print("Already guessed", guessed_word)
    elif guessed_word in word:
        print("You guessed the correct letter!")
        guessed_correctly.append(guessed_word)
    else:
        print("You have guessed a wrong letter!")
        count = count + 1
        tries = tries-1
        guessed_incorrectly.append(guessed_word)
# Printing hangman parts for each wrong guess
        for i in hang[-tries-1].split('n'):
               print(i)

if tries>0:
    print("You guessed it right")
else:
    print("You guessed the wrong letter.")
main()


  