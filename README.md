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
	int Search(char);
	void Zamena(char);
	~Stroka();
};

Stroka::Stroka()
{
	cout<<"Работает конструктор без параметров!"<<endl;
	cout<<"Введите строку (через нижние подчеруивания): ";
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

int Stroka::Search(char t)
{
	p=0;
	for (int i=0; i<strlen(s); i++)
	{
		if (s[i]==t) p++;
	}
	if (p>0) cout<<"Данный символ существует в строке!"<<endl;
	else cout<<"Такого символа в строке нет!"<<endl;
	return p;
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
	char d, j[20]; int p;
	cout<<"Введите символ, который будем искать: "; cin>>d; cout<<endl;
	Stroka z;
	z.Vyvod();
	z.VyvodSize();
	p=z.Search(d);
	if (p>0)
	{z.Zamena(d);
	z.Vyvod();}
	cout<<endl<<endl;
	Stroka x("Slovo"), c(x);
	cout<<endl;
	c.Vyvod();
	c.VyvodSize();
	p=c.Search(d);
	if (p>0)
	{c.Zamena(d);
	c.Vyvod();}
}





// var2.cpp: определяет точку входа для консольного приложения.
//

#include "stdafx.h"
#include <iostream>

using namespace std;

class Stroka
{
	char s[50], g; int r, p;
public:
	Stroka();
	void Vyvod();
	void VyvodSize();
	void SearchSlovo(char v[20]);
	~Stroka();
};

Stroka::Stroka()
{
	cout<<"Работает конструктор без параметров!"<<endl;
	cout<<"Введите строку (с нижними подчеркиванием, со знаком препинания на конце и без регистра): ";
	cin>>s; cout<<endl;
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

void Stroka::SearchSlovo(char v[20])
{
	int k=0, n=0, j=0, h=0;
	cout<<v<<endl;
	for (int i=0; i<strlen(s); i++)
	{
		if ((s[i]==v[j]) && (s[i]!='_') && (s[i]!='.') && (s[i]!=',') && (s[i]!='!') && (s[i]!='?')) { k++; j++; }
		if ((s[i]!='_') && (s[i]!='.') && (s[i]!=',') && (s[i]!='!') && (s[i]!='?')) { n++; }
		if ((s[i]=='_') || (s[i]=='.') || (s[i]=='!') || (s[i]=='?')) { if (n==k) h++; n=0; k=0; j=0; }
	}
	if (h>0) cout<<"Слово содержится в строке: "<<s<<endl;
	else cout<<"Слово не содержится в данной строке!"<<endl;
}

Stroka::~Stroka()
{
}

void _tmain(int argc, _TCHAR* argv[])
{
	setlocale(LC_ALL,"Rus");
	char d, j[20];
	cout<<"Введите слово, которое будем искать: "; cin>>j; cout<<endl;
	Stroka z[3];
	for (int i=0; i<3; i++)
	{
	z[i].Vyvod();
	z[i].VyvodSize();
	z[i].SearchSlovo(j);
	}
}

