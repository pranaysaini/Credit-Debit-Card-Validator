#include <iostream>
#include <string>

using namespace std;

bool isNumStr(const string& s) {
    int len = s.length();
    for (int i = 0; i < len; i++) {
        if (s[i] < '0' || s[i] > '9')
            return false;
    }
    return true;
}

int main() {
    string cardNum;
    
    cout<<endl;
    
    cout << "Enter 'exit' to quit." << endl;
    
    cout<<endl;
    
    while (true) {
        
        cout << "Please enter Card number to validate: ";
        cin >> cardNum;
        
        if (cardNum == "exit")
            break;
        
        else if (!isNumStr(cardNum)) {
            cout << "Bad input! ";
            continue;
        }
            
        int len = cardNum.length();
        int doubleEvenSum = 0;
        
        /* 
		The first step is to double each subsequent digit, beginning on the right. 
		If it yields a two-digit answer, sum both digits to get a one-digit result. 
		Finally, add up each response to get the "doubleEvenSum."
		*/

 
        
        for (int i = len - 2; i >= 0; i = i - 2) {
            int dbl = ((cardNum[i] - 48) * 2);
            if (dbl > 9) {
                dbl = (dbl / 10) + (dbl % 10);
            }
            doubleEvenSum += dbl;
        }
        
        /*
        In step 2 The value of "doubleEvenSum" is increased by adding each 
		    odd-numbered digit starting from the right.
		    */

           // cout;

        
        for (int i = len - 1; i >= 0; i = i - 2) {
            doubleEvenSum += (cardNum[i] - 48);
        }
        
        /* 
        Checking whether the final "doubleEvenSum" is a multiple of 10 is step three.
        If so, the credit card number is valid. Otherwise, no.
        */
         
        cout << (doubleEvenSum % 10 == 0 ? "Card Number is Valid!" : "Card Number is Invalid!") << endl;
        
        continue;        
    }

    return 0;
}
