# RSA
#include "pch.h"
#include <iostream>
#include <math.h>
#include <time.h>
using namespace std;

int main()
{
setlocale(LC_ALL, "Russian");
	int p, q, e, d, f, n, t1, t2;
	cout << "Введите 2 простых числа" << endl;
	cin >> p >> q;
	n = p * q;
	f = (p - 1)*(q - 1);
	e = f - 1;
	for (int i = 2; i < f; i++)
	{
		if ((f % i == 0) && (e % i == 0))
		{
			e--;
			i = 1;
		}
	}
	cout << "Введите цифру, которую зашифрует(P)- ";
	cin >> t1;
	cout << "Открытый ключ-{"<< e <<','<< n <<'}' << endl;
	t1 = pow(t1, e);
	t1 = t1 % n;
	t2 = t1;
	cout << "Зашифрованная цифра(E)-" << t1;
	cout << endl;
	d = 1;
	while ((d * e) % f != 0)
	{
		if ((d * e) % f == 0)
		{
			break;
		}
		else
		{
			d++;
		}
	}
	d = d + 1;
	cout << "Закрытый ключ-{" << d << ',' << n << '}' << endl;
	t2 = pow(t1, d);
	t2 = t2 % n;
	cout << "Расшифрованная цифра(P)-" << t2;
}
  
