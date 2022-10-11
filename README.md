#include<iostream>	
#include<ctime>
using namespace std;



int main() {
	srand(time(NULL));
	setlocale(LC_ALL, "Rusian");
	int rows = 20, cols = 10;
	
	int** arr = new int*[rows];
	for (int i = 0; i < rows; i++)
	{
		arr[i] = new int[cols];
	}
	for (int i = 0; i < rows;++i)
	{
		for (int d = 0; d < cols; )	// Цикл генерирует случайное число которого еще нет в массиве
		{

			bool proverka = false;
			int randnum = rand() % 200;
			for (int j = 0; j < d; j++)   //Цикл проверяет есть ли сгенерированное число в уже записанном массиве Важно проверяет не весь массив, а только те что уже записаны обрати внимание j < i
			{
				if (randnum == j) {
					proverka = true;
					break;
				}
				

			}
			if (!proverka)       //Если число уникальное записываем в массив
			{
				arr[i][d] = randnum;
				d++;
			}
			
		}

	}
	for (int i = 0; i < rows; i++)
	{
		for (int j = 0; j < cols; j++)
		{
			cout << arr[i][j] << "\t";
		}
		cout << endl;
	}
	int minNum = arr[0][0];
	for (int i = 0; i <rows ; i++)
	{
		for (int j = 0; j < cols; j++)
		{
			if (arr[i][j]< minNum)
			{
				minNum = arr[i][j];
			}
		}
	}
	cout << " Най меньшее число массива- " << minNum << endl;
	for (int i = 0; i < rows; i++)
	{
		delete[] arr[i];
	}
	delete[] arr;
}
