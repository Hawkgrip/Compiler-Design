#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main() {
    ifstream inputFile("program.cpp");

    if (!inputFile.is_open()) {
        cout << "STOP!!!!Error opening the file!" << endl;
        return 1;
    }

    const int maxUniqueFunctions = 10;
    string uniqueFunctionNames[maxUniqueFunctions];
    int uniqueFunctionsCount = 0;

    string line;

    while (getline(inputFile, line)) {
        size_t pos = line.find('(');
        if (pos != string::npos) {
            size_t spacePos = line.rfind(' ', pos);
            if (spacePos != string::npos) {
                string functionName = line.substr(spacePos + 1, pos - spacePos - 1);
                if (functionName != "main") {
                    // Check if the function name is already in the array
                    bool isUnique = true;
                    for (int i = 0; i < uniqueFunctionsCount; ++i) {
                        if (uniqueFunctionNames[i] == functionName) {
                            isUnique = false;
                            break;
                        }
                    }
                    if (isUnique && uniqueFunctionsCount < maxUniqueFunctions) {
                        uniqueFunctionNames[uniqueFunctionsCount++] = functionName;
                    }
                }
            }
        }
    }

    cout << "Unique User-Defined Function Names:" << endl;
    for (int i = 0; i < uniqueFunctionsCount; ++i) {
        cout << uniqueFunctionNames[i] << endl;
    }

    cout << "Total number of user-defined functions: " << uniqueFunctionsCount << endl;

    inputFile.close();
    return 0;
}
