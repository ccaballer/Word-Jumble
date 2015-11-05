# Word-Jumble
Review and practicing it.
#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>
using namespace std;
int main() {
	enum fields {Word, Hint, Num_Fields};
	const int Num_Words = 5;
	const string Words[Num_Words][Num_Fields] = {
		{"wall", " Do you feel banging your head against something?"},
		{"Break","sinonim of destroy"},
		{"Couch","Where you and your friend sit to watch tv"},
		{"Potato","Banana and... ask a minion"},
		{"monkeys","got your keys in monday"}
	};
	enum difficulty{ Easy,Medium,Hard,Num_Diff_Levels};
	cout << "There are " << Num_Diff_Levels << " Difficulty Levels.\n";
		srand(time(0));
		int choice = (rand() % Num_Words);
		string theWord = Words[choice][Word];
		string theHint = Words[choice][Hint];
		string jumble = theWord;
		int length = jumble.size();
		for (int i = 0; i < length; ++i) {
			int index1 = (rand() % length);
			int index2 = (rand() % length);	
			char temp = jumble[index1];
			jumble[index1] = jumble[index2];
			jumble[index2] = temp;
		}
		cout<<"\t Welcome to Word Jumble \n\n";
		cout << "Unscramble the letters to make a word. \n";
		cout << "Enter 'hint' for a hint\n";
		cout << "Enter 'quit' to quit the game.\n";	
		cout << " The jumble is: " << jumble;
		string guess;
		cout << "\n\n Your guess: ";
			cin >> guess;
			while ((guess != theWord) && (guess != "quit")) {
				if (guess == "hint")
					cout << theHint;
				else cout << "Sorry, that's not it.";
				cout << "\n\nYour guess: ";
				cin >> guess;

			}
			if (guess == theWord)
				cout << "\nThat's it! You guessed it.\n";
			return (EXIT_SUCCESS);
}


