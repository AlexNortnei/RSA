# RSA
#include "pch.h"
#include <iostream>
#include <math.h>
#include <time.h>
using namespace std;
/*int EVK(int a, int b)//Алгоритм Евклида
{
	int c;
	while (b)
	{
		c = a % b;
		a = b;
		b = c;
	}
	return abs(a);
}*/


int main()
{
	setlocale(LC_ALL, "Russian");
	int p, q, n, f, e, d,P;
	unsigned long long T;
	cout << "Введите два простых числа" << endl;
	cin >> p >> q;
	cout << "Введите сообщение (число), желаемое зашифровать и расшифровать." << endl;
	cin >> T;
	n = p * q;
	f = (p - 1)*(q - 1);
	e = 1;
	int v = 0;;
	while (v != 1)
	{
		if ((f % 2) == 1)
		{
			e = 2;
			v = 1;
		}
		if ((f % 2) == 0)
		{
			e = 3;
			v = 1;
		} 
		//e--;
		//v = EVK(e, f);
	}
	T = pow(T, e);
	T = T % n;
	cout << "Зашифрованное сообщение " << T << endl;
	d = 1;	
	while (((d*e) % f) != 1)
	{
		d++;
	}
	T = pow(T, d);
	T = T % n;
	cout << "Расшифрованное сообщение " << T << endl;
	cout << "Открытый ключ - {" << e << ',' << n << '}' << endl;
	cout << "Закрытый ключ - {" << d << ',' << n << '}';
	
}
  
