ADT - Abstract Data Type
-----------------------

Exempel på ADT:
	Lista
	Stack
	Kö
    Prioritetskö
	Heap

Interface
---------

Ex: ADT Lista

IList.h:
```C++
#ifndef ILIST_H
#define ILIST_H
template<typename T>
class IList {
	virtual void insertAll(int pos, T element) = 0;
	virtual T elementAt(int pos)const = 0;
	virtual T removeAt(int pos) = 0;
	virtual int size()const = 0;
};

List.h
class List:public IList<T> {

};
#endif
```

Stack
-----

Följer principen LIFO(Last In First Out)

IStack.h:
```C++
#ifndef ISTACK_H
#define ISTACK_H

template<typename T>
class IStack {
	virtual void push(const T &element) = 0;
	virtual T pop()const throw(...)  = 0;
	virtual T peak()const throw(...) = 0;
	virtual bool isEmpty()const = 0;
};
#endif
```

Kö
---
Följer principen FIFO

Länkad struktur
-----
En node har två egenskaper, den kan ha ett värde och en pointer.
När man har flera noder på pekar pekaren i nod ett på värdet av node två.

Den första i listan är bara en pekare och den sista blir en nullpointer.

Rekursion

-----


Ex:
```C++
void info(int nr) {
	if(nr > 0) {
		cout << "nr är nu: " << nr << endl;
		info(nr-1);
	}
}

int main() {
	info(5);
	return 0;
}
```

Man måste ha ett basfall som stoppar rekursionen.

Rekursiv sortering
-----

Välj ett pivot värde.
Stortera så att det som är mindre än pivot värdet till vänster och det som är större ligger till höger. Detta upprepas rekursivt för varje halva.

#####Val av pivot värde
Finns många sätt att göra detta, i detta fallet testar vi med det första värdet.

#####Grov sortering
Man sorterar först grovt, om nummret är lägre ska det till till vänster om pivot värdet. Samma gäller fast tvärtom.

När man ska byta plats i arrayen så är det smidigast att flytta det lägre värdet precis till höger om pivotvärdet. Då kan det mindre värdet och pivotvärdet byta plats.

Efter detta sorterar man på samma sätt på var sida om pivot värdet.


