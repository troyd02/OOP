Решетко Дмитрий, 7 группа, ДЭиВИ

// var1.cpp: определяет точку входа для консольного приложения.
//

#include "stdafx.h"
#include <iostream>

using namespace std;

class Stroka
{
	char s[50], g; int r, p;
public:
	Stroka();
	Stroka(char *);
	Stroka(const Stroka &);
	void Vyvod();
	void VyvodSize();
	void Search(char);
	void Zamena(char);
	~Stroka();
};

Stroka::Stroka()
{
	cout<<"Работает конструктор без параметров!"<<endl;
	cout<<"Введите строку: ";
	cin>>s; cout<<endl;
}

Stroka::Stroka(char *q)
{
	cout<<"Работает конструктор с параметром!"<<endl;
	strcpy_s(s, q);
}

Stroka::Stroka(const Stroka & w)
{
	
	cout<<"Работает конструктор копии!"<<endl;
	strcpy_s(s, w.s);
}

void Stroka::Vyvod()
{
	cout<<"Строка: "<<s<<endl;
}

void Stroka::VyvodSize()
{
	r=strlen(s);
	cout<<"Длиннa строки: "<<r<<endl;
}

void Stroka::Search(char t)
{
	p=0;
	for (int i=0; i<strlen(s); i++)
	{
		if (s[i]==t) p++;
	}
	if (p>0) cout<<"Данный символ существует в строке!"<<endl;
	else cout<<"Такого символа в строке нет!"<<endl;
}

void Stroka::Zamena(char f)
{
	cout<<"Введите букву, которую хотите заменить: "; cin>>g;
	for (int i=0; i<strlen(s); i++)
	{
		if (s[i]==f) s[i]=g;
	}
}

Stroka::~Stroka()
{
}

void _tmain(int argc, _TCHAR* argv[])
{
	setlocale(LC_ALL,"Rus");
	char d;
	cout<<"Введите символ, который будем искать: "; cin>>d; cout<<endl;
	Stroka z[3], x("Slovo"), c(x);
	for (int i=0; i<3; i++)
	{
	z[i].Vyvod();
	z[i].VyvodSize();
	z[i].Search(d);
	z[i].Zamena(d);
	z[i].Vyvod();
	}
	cout<<endl;
	c.Vyvod();
	c.VyvodSize();
	c.Search(d);
	c.Zamena(d);
	c.Vyvod();


}
