#include <iostream>
#include <cstring>
#include <cctype>
using namespace std;

int main()
{
    char password[100];

    bool hasUpper = false;
    bool hasLower = false;
    bool hasDigit = false;
    bool hasSpecial = false;

    cout << "Enter your password: ";
    cin.getline(password, 100);

    int length = strlen(password);

    for(int i = 0; i < length; i++) {
        if(isupper(password[i]))
            hasUpper = true;
        else if(islower(password[i]))
            hasLower = true;
        else if(isdigit(password[i]))
            hasDigit = true;
        else
            hasSpecial = true;
    }

    cout << "\n--- Password Analysis ---\n";

    if(length < 8) {
        cout << "Password Length: Weak (minimum 8 characters required)\n";
    } else {
        cout << "Password Length: OK\n";
    }

    cout << "Uppercase Letter: " << (hasUpper ? "Present" : "Missing") << endl;
    cout << "Lowercase Letter: " << (hasLower ? "Present" : "Missing") << endl;
    cout << "Digit: " << (hasDigit ? "Present" : "Missing") << endl;
    cout << "Special Character: " << (hasSpecial ? "Present" : "Missing") << endl;

    int score = 0;
    if(length >= 8) score++;
    if(hasUpper) score++;
    if(hasLower) score++;
    if(hasDigit) score++;
    if(hasSpecial) score++;

    cout << "\nPassword Strength: ";

    if(score <= 2)
        cout << "WEAK";
    else if(score == 3 || score == 4)
        cout << "MEDIUM";
    else
        cout << "STRONG";

    cout << endl;

    return 0;
}
