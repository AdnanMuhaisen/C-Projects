#include <iostream>
#include <cmath>
#include<cstdlib>

using namespace std;

enum enQuestionsLevel { easy = 1, mid = 2, hard = 3 };
enum enOperations{addition=1,subtraction=2,multiplication=3,division=4,mix=5};

void tab() {
	cout << "\n-------------------------------------\n" << endl;
}

int generateNumber(int from, int to) {
	return rand() % (to - from + 1) + from;
}

int generateOperation() {
	return generateNumber(1, 4);
}

char getOperation(int o) {
	switch (o) {
	case 1:
		return '+';
	case 2:
		return '-';
	case 3:
		return'*';
	case 4:
		return '/';
	}
}

bool additionOperation(int num1,int num2) {
	int result;
	cout << num1<<" + " << num2 << " = ?";
	cin >> result;
	if (result == num1 + num2) {
		return true;
	}
	else {
		return false;
	}
}

bool subtractionOperation(int num1, int num2) {
	int result;
	cout << num1 << " - " << num2 << " = ?";
	cin >> result;
	if (result == num1 - num2) {
		return true;
	}
	else {
		return false;
	}
}

bool multiplicationOperation(int num1, int num2) {
	int result;
	cout << num1 << " * " << num2 << " = ?";
	cin >> result;
	if (result == num1 * num2) {
		return true;
	}
	else {
		return false;
	}
}

bool divisionOperation(int num1, int num2) {
	int result;
	cout << num1 << " / " << num2 << " = ?";
	cin >> result;
	if (result == num1 / num2) {
		return true;
	}
	else {
		return false;
	}
}

void rightAnswer() {
	//tab();
	system("color 27");
	cout << "\nRight Answer :)\n" << endl;
	tab();
}

void wrongAnswer(int num1,int num2,int operation) {
//	tab();
	cout << "\a";
	system("color 47");
	cout << "\nWrong Answer :(" << endl;
	switch (operation) {
	case 1:
		cout << "The Right Answer Is : " << num1 + num2 << endl;
		break;
	case 2:
		cout << "The Right Answer Is : " << num1 - num2 << endl;
		break;
	case 3:
		cout << "The Right Answer Is : " << num1 * num2 << endl;
		break;
	case 4:
		cout << "The Right Answer Is : " << num1 / num2 << endl;
		break;
	}
	cout << "\n";
	tab();
}

void easyQuestion(int& rightQ,int& wrongQ,int operation) {
	int num1 = generateNumber(0, 9), num2 = generateNumber(0, 9);

	if (operation == enOperations::division && num2 == 0) {
		num2 = generateNumber(1, 9);
	}

	if (operation == enOperations::addition) {
		if (additionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::addition);
			wrongQ++;
		}
	}
	else if (operation == enOperations::subtraction) {
		if (subtractionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::subtraction);
			wrongQ++;
		}
	}
	else if (operation == enOperations::multiplication) {
		if (multiplicationOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::multiplication);
			wrongQ++;
		}
	}
	else if (operation == enOperations::division) {
		if (divisionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::division);
			wrongQ++;
		}
	}
}

void midQuestion(int& rightQ, int& wrongQ, int operation) {
	int num1 = generateNumber(0, 100), num2 = generateNumber(0, 100);

	if (operation == enOperations::division && num2 == 0) {
		num2 = generateNumber(1, 100);
	}
	if (operation == enOperations::addition) {
		if (additionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::addition);
			wrongQ++;
		}
	}
	else if (operation == enOperations::subtraction) {
		if (subtractionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::subtraction);
			wrongQ++;
		}
	}
	else if (operation == enOperations::multiplication) {
		if (multiplicationOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::multiplication);
			wrongQ++;
		}
	}
	else if (operation == enOperations::division) {
		if (divisionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::division);
			wrongQ++;
		}
	}
}

void hardQuestion(int& rightQ, int& wrongQ, int operation) {
	int num1 = generateNumber(100, 1000), num2 = generateNumber(100, 1000);

	if (operation == enOperations::division && num2 == 0) {
		num2 = generateNumber(1, 1000);
	}
	if (operation == enOperations::addition) {
		if (additionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::addition);
			wrongQ++;
		}
	}
	else if (operation == enOperations::subtraction) {
		if (subtractionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::subtraction);
			wrongQ++;
		}
	}
	else if (operation == enOperations::multiplication) {
		if (multiplicationOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::multiplication);
			wrongQ++;
		}
	}
	else if (operation == enOperations::division) {
		if (divisionOperation(num1, num2)) {
			rightAnswer();
			rightQ++;
		}
		else {
			wrongAnswer(num1, num2, enOperations::division);
			wrongQ++;
		}
	}
}

void mixEasyQuestion(int& rightQ, int& wrongQ) {
	int randomOperation = generateNumber(1, 4);
	easyQuestion(rightQ, wrongQ, randomOperation);
}

void mixMidQuestion(int& rightQ, int& wrongQ) {
	int randomOperation = generateNumber(1, 4);
	midQuestion(rightQ, wrongQ, randomOperation);
}

void mixHardQuestion(int& rightQ, int& wrongQ) {
	int randomOperation = generateNumber(1, 4);
	hardQuestion(rightQ, wrongQ, randomOperation);
}

bool endOfTheGame(int right,int wrong) {

	double avarage = (double)right / (right + wrong); bool again;
	cout << "RESULTS : \n" << endl;
	if (right >= wrong) {
		system("color 27");
		cout << "CONGRATS $$" << endl;
	}
	else {
		system("color 47");
		cout << "GOOD LUCK IN AOTHER ROUNDS" << endl;
	}
	cout << "Number of Right answers : " << right << " :)" << endl;
	cout << "Number of Wrong answers : " << wrong << " :(" << endl;
	cout << "Your Avarge = " << avarage <<" Out Of "<<(right+wrong)<< endl;

	tab();

	cout << "Are You Want To Play Again[1]YES,[0]NO ? ";
	cin >> again;
	return again;
}

void play() {
	int right = 0, wrong = 0, numberOfRounds, qLevel, operationType;
	cout << "Enter The Number Of Qusetions : ";
	cin >> numberOfRounds; cout << endl;
	cout << "The Level Of The Questions You Want Easy[1] Mid[2] Hard[3] : ";
	cin >> qLevel; cout << endl;
	cout << "Enter Operation Type Addition[1] Subtraction[2] Multiplication[3] Division[4] Mix[5] : ";
	cin >> operationType; cout << endl;

	for (size_t i = 1; i <= numberOfRounds; i++)
	{

		cout << "Question [" << i << "/" << numberOfRounds << "] : " << endl;
		if (qLevel == enQuestionsLevel::easy) {
			if (operationType == enOperations::mix) {
				mixEasyQuestion(right, wrong);
			}
			else {
				easyQuestion(right, wrong,operationType);
			}
		}
		else if (qLevel == enQuestionsLevel::mid) {
			if (operationType == enOperations::mix) {
				mixMidQuestion(right, wrong);
			}
			else {
				midQuestion(right, wrong, operationType);
			}
		}
		else if (qLevel == enQuestionsLevel::hard) {
			if (operationType == enOperations::mix) {
				mixHardQuestion(right, wrong);
			}
			else {
				hardQuestion(right, wrong, operationType);
			}
		}
		system("cls");
	}
	tab();
	
	if (endOfTheGame(right, wrong)) {
		system("color 07");
		play();
	}
	else {
		system("color 07");
		cout << "GOOD BYE !!" << endl;
	}
}

int main()
{
	srand((unsigned)time(NULL));
	play();
}
