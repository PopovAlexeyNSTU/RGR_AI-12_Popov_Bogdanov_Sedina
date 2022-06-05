#include <iostream>
#include <fstream>
#include <cmath>
#include <string>

using namespace std;

int decimal_transfer(const string &line) {
    int result = 0;
    for (size_t i = 0; i <= 8; i++) {
        if (line[i] == '1') {
            result += pow(2, i);
        }
    }
    return result;
}

string binary_translation(int ch) {
    string binary_number;
    while (ch != 0) {
        if (ch % 2 == 0) {
            binary_number.append("0");
        } else {
            binary_number.append("1");
        }
        ch = ch / 2;
    }
    while (binary_number.size() != 8) {
        binary_number.append("0");
    }
    return binary_number;
}

void encryption(const string &path_in, const string &path_out) {
    ifstream fin;
    ofstream fout;
    fin.open(path_in);
    fout.open(path_out);
    if (!fin.is_open()) {
        cout << "Не удалось найти файл для 'path_in' !!!" << endl;
    } else if (!fout.is_open()) {
        cout << "Не удалось найти файл для 'path_out' !!!" << endl;
    } else {
        string str;
        string ch;
        while (!fin.eof())
        {
            str = "";
            getline(fin, str);
            for (size_t i = 0; i < str.size(); i++) {
                ch = binary_translation(int(str[i]));
                fout << ch;
            }
        }
        fin.close();
        fout.close();
    }
}

void decryption(const string &path_in, const string &path_out) {
    ifstream fin;
    ofstream fout;
    fin.open(path_in);
    fout.open(path_out);
    if (!fin.is_open()) {
        cout << "Не удалось найти файл для 'path_in' !!!" << endl;
    } else if (!fout.is_open()) {
        cout << "Не удалось найти файл для 'path_out' !!!" << endl;
    } else {
        string str;
        while (!fin.eof())
        {
            str = "";
            getline(fin, str);
            for (size_t i = 0; i < str.size();) {
                string ch;
                for (size_t j = 0; j < 8; j++, i++) {
                    ch.push_back(str[i]);
                }
                fout << static_cast<char>(decimal_transfer(ch));
            }
        }
        fin.close();
        fout.close();
    }
}

void create_file() {
    string path;
    string data;
    cout << "Укажите путь до нового файла: ";
    cin >> path;
    if (char(cin.peek()) == '\n')
        cin.ignore();

    if (cin.fail()) {
        cin.clear();
        cin.ignore(32767, '\n');
    }
    cout << "Введите данные: ";
    getline(cin, data);
    std::ofstream out;
    out.open(path);
    if (!out.is_open()) {
        cout << "Не удалось найти файл!!!" << endl;
    } else {
        out << data;
        out.close();
    }
}

void read_path_sh() {
    string path_in;
    string path_out;
    cout << "Укажите путь, откуда будут читаться данные: "; cin >> path_in;
    cout << "Укажите путь, куда будут записываться данные: "; cin >> path_out;
    encryption(path_in, path_out);
}

void read_path_unsh() {
    string path_in;
    string path_out;
    cout << "Укажите путь, откуда будут читаться данные: "; cin >> path_in;
    cout << "Укажите путь, куда будут записываться данные: "; cin >> path_out;
    decryption(path_in, path_out);
}

int main() {
    int key;
    while (true) {
        cout << "Выберите действие:" << endl << "1. Создание текстового файла" << endl << "2. Шифрование данных"
             << endl << "3. Дешифрование даннных" << endl << "4. Выход" << endl << "> ";
        cin >> key;
        while (key < 1 || key > 4) {
            cin >> key;
        }
        if (key == 1) {
            create_file();
        } else if (key == 2) {
            read_path_sh();
        } else if (key == 3) {
            read_path_unsh();
        } else if (key == 4) {
            break;
        }
    }
    return 0;
}
