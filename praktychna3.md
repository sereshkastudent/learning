
# Практична робота 3

## Алгоритми сортування на мові java
![alt](https://cojo.ru/wp-content/uploads/2023/01/kartinka-pomogite-3.webp)
`print('help please!!!')`
```

```javascript
// підсвітка коду JavaScript
var foo = 'bar';
```


Товар     | Ціна
--------- | -----
Ноутбук   | $1600
Смартфон  | $150
Принтер   | $75

Markdown
: Інструмент перетворення тексту в HTML

Філософія Markdown
: Мова `Markdown` покликана бути такою ж простою для читання та простотою для написання, наскільки це можливо

StackEdit
: Редактор `Markdown` в браузері

Автори
: Джон Грубер
: Бенуа Швеблін

### 3 алгоритми сортування мовою С++

```
#include <iostream>
using namespace std;

//ф-ция для обмена значений ячеек
void swapEl(int *arr, int i)
{
	int buff;
	buff = arr[i];
	arr[i] = arr[i - 1];
	arr[i - 1] = buff;
}

//ф-ция "шейкер"-сортировки
void myShakerSort(int *arr, int size)
{
	int leftMark = 1;
	int rightMark = size - 1;
	while (leftMark <= rightMark)
	{
		for (int i = rightMark; i >= leftMark; i--)
		if (arr[i - 1] > arr[i]) swapEl(arr, i);
		leftMark++;


		for (int i = leftMark; i <= rightMark; i++)
		if (arr[i - 1] > arr[i]) swapEl(arr, i);
		rightMark--;

		cout << "\nИтерация: " << leftMark - 1; // просмотр количества итераций
	}
}

int main()
{
	setlocale(LC_ALL, "rus");

	int size = 0;
	cout << "Размер массива: ";
	cin >> size;
	int *A = new int[size];

	for (int k = 0; k < size; k++)
	{
		A[k] = size - k; // запись значений по убыванию
		cout << A[k]  << " | ";
	}

	myShakerSort(A, size); // сортировка

	cout << "\nМассив после сортировки:\n";
	for (int k = 0; k < size; k++)
	{
		cout << A[k] << " | ";
	}
	cout << endl;
	return 0;
}
```

```
#include <iostream>
using namespace std;

int main()
{
	const int N = 10;
	int a[N] = { 12, 5, 3, 2, 45, 96, 6, 8, 11, 24 };

	int buff = 0;	// для хранения перемещаемого значения
	int i, j;		// для циклов		

	/************* Начало сортировки *******************/
	for (i = 1; i < N; i++)
	{
		buff = a[i]; // запомним обрабатываемый элемент
		// и начнем перемещение элементов слева от него
		// пока запомненный не окажется меньше чем перемещаемый
		for (j = i - 1; j >= 0 && a[j] > buff; j--)
					a[j + 1] = a[j];	

		a[j + 1] = buff; // и поставим запомненный на его новое место	
	}
	/************* Конец сортировки *******************/

	for (int i = 0; i < N; i++) // вывод отсортированного массива
		cout << a[i] << '\t';
	cout << endl;
}
```

```
#include <iostream>
using namespace std;

int main()
{
	const int N = 10;
	int a[N] = { 1, 25, 6, 32, 43, 5, 96, 23, 4, 55 };
	
	int min = 0;	// для записи минимального значения
	int buf = 0;	// для обмена значениями 

	/*********** Начало сортировки **************/
	for (int i = 0; i < N; i++)
	{
		min = i; // запомним номер текущей ячейки, как ячейки с минимальным значением
		// в цикле найдем реальный номер ячейки с минимальным значением
		for (int j = i + 1; j < N; j++)
			min = ( a[j] < a[min] ) ? j : min;
		// cделаем перестановку этого элемента, поменяв его местами с текущим
		if (i != min)
		{
			buf = a[i];
			a[i] = a[min];
			a[min] = buf;
		}
	}
	/*********** Конец сортировки **************/

	for (int i = 0; i < N; i++) 	//Вывод отсортированного массива
		cout << a[i] << '\t';
	cout << endl;
}
```
