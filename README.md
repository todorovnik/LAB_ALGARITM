# LAB_ALGARITM
ВСЕ ЛАБОРАТОРНЫЕ РАБОТЫ
Matrix30.
#include <iostream>
#include <vector>

using namespace std;
const int M = 20, N = 20; //максимальне кількість рядків стовпців

int main() {
    int m, n;
    cout << "Введіть кількість рядків (максимум " << M << "): ";
    cin >> m;
    cout << "Введіть кількість стовпців (максимум " << N << "): ";
    cin >> n;
    cout << "Введіть розміри матриці (MxN)" << m << "x" << n << ":" << endl;

    // Створюємо матрицю та заповнюємо її
    vector<vector<int>> matrix(m, vector<int>(n));
    cout << "Введіть елементи матриці:\n";
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            cin >> matrix[i][j];
        }
    }

    // Обчислюємо середнє арифметичне для кожного стовпця
    vector<double> column_average(n);
    for (int j = 0; j < n; j++) {
        double sum = 0;
        for (int i = 0; i < m; i++) {
            sum += matrix[i][j];
        }
        column_average[j] = sum / m;
        cout << column_average[j] << " ";
    }

    // Знаходимо кількість елементів в кожному стовпці,
    // що більше за середнє арифметичне цього стовпця
    vector<int> greater_than_average(n);
    for (int j = 0; j < n; j++) {
        int count = 0;
        for (int i = 0; i < m; i++) {
            if (matrix[i][j] > column_average[j]) {
                count++;
            }
        }
        greater_than_average[j] = count;
    }

    // Виводимо результати
    cout << "Кількість елементів, більших за середнє арифметичне кожного стовпця:\n";
    for (int j = 0; j < n; j++) {
        cout << greater_than_average[j] << " ";
    }
    cout << endl;

    return 0;
}

Matrix71.
#include <iostream>
using namespace std;

int main() {
    int M, N;
    cout << "Введите размеры матрицы (MxN): ";
    cin >> M >> N;

    int matrix[M][N];

    // Читання елементів матриці з введення користувача
    cout << "Введите элементы матрицы:" << endl;
    for (int i = 0; i < M; i++) {
        for (int j = 0; j < N; j++) {
            cin >> matrix[i][j];
        }
    }

    // Знаходження мінімального елемента та індексу його стовпця
    int min_element = matrix[0][0], min_column = 0;
    for (int j = 0; j < N; j++) {
        if (matrix[0][j] < min_element) {
            min_element = matrix[0][j];
            min_column = j;
        }
    }

    // Створення нової матриці
    int new_matrix[M][1]; // Матриця розміром Mx1 для зберігання стовпця
    for (int i = 0; i < M; i++) {
        new_matrix[i][0] = matrix[i][min_column]; // Записуємо значення в стовпець нової матриці
    }

    // Вивід нової матриці
    cout << "Стовпець з мінімальними значеннями:" << endl;
    for (int i = 0; i < M; i++) {
        cout << new_matrix[i][0] << endl; // Виводимо значення стовпця нової матриці
    }
    
    return 0;
}

1)Array 30
#include <stdio.h>
int main(void)
{
    float a[10];
 
    int n;
 
    printf("N: ");
    scanf("%i",&n);
 
    int i;
    for (i=0; i<n; ++i){
        printf("a[%i] : ",i+1);
        scanf("%f",&a[i]);
    }
 
    float ai1,ai=a[0];
    a[0]=(ai+a[1])/2;
    for (i=1; i<n-1; ++i){
            ai1=ai;
            ai=a[i];
            a[i]=(ai1+ai+a[i+1])/3;
    }
 
    a[n-1]=(a[n-1]+ai)/2;
 
    printf("A: \n");
    for (i=0; i<n; ++i) printf("  %i: %f\n",i+1,a[i]);
 
    return 0;
}

2)Matrix78

#include <iostream>

using namespace std;



int main() {

    const int M = 4;

    int matrix[M][M] = {{1, 2, 3, 4},

                        {5, 6, 7, 8},

                        {9, 10, 11, 12},

                        {13, 14, 15, 16}};

    

    for (int i = 0; i < M; i++) {

        for (int j = 0; j < M; j++) {

            if (i + j >= M) {  // елементи під побічною діагоналлю

                matrix[i][j] = 0;

            }

        }

    }



    // виведення зміненої матриці

    for (int i = 0; i < M; i++) {

        for (int j = 0; j < M; j++) {

            cout << matrix[i][j] << " ";

        }

        cout << endl;

    }

    

    return 0;

}

3)#include <iostream>
using namespace std;

int main() {
    const int M = 4;
    int matrix[M][M] = {{1, 2, 3, 4},
                        {5, 6, 7, 8},
                        {9, 10, 11, 12},
                        {13, 14, 15, 16}};
    
    for (int i = 0; i < M; i++) {
        for (int j = 0; j < M; j++) {
            if (i + j >= M) {  // елементи під побічною діагоналлю
                matrix[i][j] = 0;
            }
        }
    }

    // виведення зміненої матриці
    for (int i = 0; i < M; i++) {
        for (int j = 0; j < M; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
    
    return 0;
}

3 Задание
#include <iostream>



using namespace std;



const int ROWS = 4; // Кількість рядків матриці

const int COLS = 4; // Кількість стовпців матриці



void selectionSortMatrix(double matrix[][COLS], int rows, int cols) {

    int min_idx;



    // Перебираємо всі елементи матриці

    for (int i = 0; i < ROWS; i++) {

        for (int j = 0; j < COLS; j++) {

            min_idx = j;

            // Знаходимо мінімальний елемент в невідсортованій частині матриці

            for (int k = j + 1; k < COLS; k++) {

                if (matrix[i][k] < matrix[i][min_idx])

                    min_idx = k;

            }



            // Міняємо місцями мінімальний елемент із першим елементом невідсортованої частини матриці

            double temp = matrix[i][min_idx];

            matrix[i][min_idx] = matrix[i][j];

            matrix[i][j] = temp;

        }

    }

}



int main() {

    double matrix[ROWS][COLS] = {

        {15, 7, 2, 9},

        {3, 8, 5, 12},

        {14, 8, 1, 18},

        {8, 4, 15, 7}

    };



    cout << "Початкова матриця:" << endl;

    for (int i = 0; i < ROWS; i++) {

        for (int j = 0; j < COLS; j++) {

            cout << matrix[i][j] << " ";

        }

        cout << endl;

    }



    selectionSortMatrix(matrix, ROWS, COLS);



    cout << "Відсортована матриця:" << endl;

    for (int i = 0; i < ROWS; i++) {

        for (int j = 0; j < COLS; j++) {

            cout << matrix[i][j] << " ";

        }

        cout << endl;

    }



    return 0;

}

4)#include <iostream>

#include <algorithm> // for std::sort



using namespace std;



const int MAX_SIZE = 100; // Максимальна розмірність масиву



int main() {

    int n;

    int arr[MAX_SIZE];



    cout << "Введіть кількість елементів масиву (не більше " << MAX_SIZE << "): ";

    cin >> n;



    // Перевірка на допустиму розмірність масиву

    if (n > MAX_SIZE || n <= 0) {

        cout << "Помилка: неприпустима розмірність масиву!" << endl;

        return 1;

    }



    // Введення елементів масиву

    cout << "Введіть " << n << " елементів масиву: ";

    for (int i = 0; i < n; i++) {

        cin >> arr[i];

    }



    // Виведення введеного масиву

    cout << "Введений масив: ";

    for (int i = 0; i < n; i++) {

        cout << arr[i] << " ";

    }

    cout << endl;



    // Сортування методом вибору

    int min_idx;

    for (int i = 0; i < n - 1; i++) {

        min_idx = i;

        for (int j = i + 1; j < n; j++) {

            if (arr[j] < arr[min_idx])

                min_idx = j;

        }

        swap(arr[i], arr[min_idx]);

    }



    // Виведення відсортованого масиву

    cout << "Відсортований масив: ";

    for (int i = 0; i < n; i++) {

        cout << arr[i] << " ";

    }

    cout << endl;



    return 0;
                
   #include <iostream>
#include <string>
#include <fstream>

using namespace std;
const int max_size = 200;


void get_string_for_find(char s[max_size], char s1[max_size], int& position, int& n) {//Функция для ввода строк для Задания 1
    cout << "Введите строку в которой искать: ";
    cin.get();//Создаем поток для считывания с консоли
    gets_s(s, max_size);//Считывания всех элементов записаных в строку и запись по элементно в массив
    cout << "Введите набор символов которые искать: ";
    gets_s(s1, max_size);//Считывания всех элементов записаных в строку и запись по элементно в массив
    cout << "Введите позицию с которой начинать поиск: ";
    cin >> position;
    cout << "Введите количество символов для поиска: ";
    cin >> n;
}
int my_string_method(const char* s, const char* s1, int leng, int position, int n) {
    for (int i = position; i < leng; i++) {//Проходим по строке в которой ищем (начиная с заданой позиции)
        for (int j = 0; j < n; j++) {//Проходим по массиву символов(До заданого символа)
            if (s[i] == s1[j]) {//Если символы совпали
                return i;//возвращаем позицию первого вхождения символа в строку
            }
        }
    }
    return -1;//возвращаем -1 если совпадения символов не найдены
}
void task1() {
    char s[max_size], s1[max_size];
    int position, n;
    get_string_for_find(s, s1, position, n);
    string str = s; //Строку в которой искать превращаем в тип string
    int leng = str.length(); //находим длинну строки
    cout << "Поиск позиции в строке: " << str.find_first_of(s1, position) << endl; //Функция из библиотеки <string>
    cout << "Метод из библиотеки с массивом: " << my_string_method(s, s1, leng, position, n); //Аналог функции из библиотеки <string>

}

void task2() {
    ifstream input("lab9.txt"); // открываем файл для чтения
    string str;
    getline(input, str); // считываем строку из файла
    input.close(); // закрываем файл

    int num = stoi(str); // преобразуем строку в число
    string binary = ""; // создаем пустую строку для хранения двоичного представления

    while (num > 0) { // пока число не станет равным 0
        int remainder = num % 2; // находим остаток от деления на 2
        num /= 2; // делим число на 2
        binary = to_string(remainder) + binary; // добавляем остаток в начало строки
    }

    cout << binary << endl; // выводим двоичное представление числа на экран

    }

int main() {
    setlocale(LC_ALL, "rus");
    int menu;
    do
    {
        cout << "\n[0] - EXIT \t\t\n[1] - Задание 1 \t\n[2] - Задание 2\n";
        cout << "Выберите задания: ";
        cin >> menu;
        switch (menu) {
        case 1: task1(); break;
        case 2: task2(); break;
        case 0: cout << "Выход...." << endl; break;
        default: cout << "Ошибка!!!" << endl;
        }
    } while (menu != 0);
    return 0;
}

#include<iostream>
#include<cmath>
#include<math.h>

using namespace std;

// описание структуры
struct TTime {
    int Hour;
    int Min;
    int Sec;
};

// проверка на корректность
int CheckTime(TTime T) {
    if (T.Hour < 0 || T.Hour > 23) {
        return 1;
    }
    if (T.Min < 0 || T.Min > 59) {
        return 2;
    }
    if (T.Sec < 0 || T.Sec > 59) {
        return 3;
    }
    return 0;
}

// функция реализации задания
void PrevMin(TTime& T) {
    if (CheckTime(T) != 0) {
        return;
    }
    T.Min--;
    if (T.Min < 0) {
        T.Min = 59;
        T.Hour--;
        if (T.Hour < 0) {
            T.Hour = 23;
        }
    }
}

void task1() {
    TTime T1 = { 15, 30, 45 };
    TTime T2 = { 25, 10, 20 };
    TTime T3 = { 8, 65, 10 };
    TTime T4 = { 22, 40, 70 };
    TTime T5 = { 11, 20, 30 };
    PrevMin(T1);
    PrevMin(T2);
    PrevMin(T3);
    PrevMin(T4);
    PrevMin(T5);
    cout << T1.Hour << ":" << T1.Min << ":" << T1.Sec << endl; 
    cout << T2.Hour << ":" << T2.Min << ":" << T2.Sec << endl; 
    cout << T3.Hour << ":" << T3.Min << ":" << T3.Sec << endl; 
    cout << T4.Hour << ":" << T4.Min << ":" << T4.Sec << endl; 
    cout << T5.Hour << ":" << T5.Min << ":" << T5.Sec << endl; 
}

struct Ftask2 {
    int A, A2, A3, A5, A10, A15;

    void calculate() {
        A2 = A * A;
        A3 = A * A2;
        A5 = A2 * A3;
        A10 = A5 * A5;
        A15 = A10 * A5;
    }
    void printResult() {
        cout << "A^2: " << A2 << endl;
        cout << "A^3: " << A3 << endl;
        cout << "A^5: " << A5 << endl;
        cout << "A^10: " << A10 << endl;
        cout << "A^15: " << A15 << endl;    }
};
void task2() {
    Ftask2 ft2;
    cout << "Введите число: ";
    cin >> ft2.A;
    ft2.calculate();
    ft2.printResult();
}

struct Ftask3 {
    float A, B, C;
    bool Rtask3() {
        return ((A + B > C && B + C > A && C + A > B));
    }
};
void task3() {
    Ftask3 ft3;
    cout << "Введите три числа: ";
    cin >> ft3.A >> ft3.B >> ft3.C;
    cout << "Результат: " << ft3.Rtask3() << endl;
}


int main() {
    setlocale(LC_ALL, "rus");
    int menu;
    do
    {
        cout << "\n[0] - EXIT \t\t\n[1] - Задание 1 \t\n[2] - Задание 2 \t\n[3] - Задание 3\n";
        cout << "Выберите задания: ";
        cin >> menu;
        switch (menu) {
        case 1: task1(); break;
        case 2: task2(); break;
        case 3: task3(); break;
        case 0: cout << "Выход...." << endl; break;
        default: cout << "Ошибка!!!" << endl;
        }
    } while (menu != 0);
}
