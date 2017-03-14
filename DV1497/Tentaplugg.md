Rand
-----
```
#include <ctime> eller #include <time.h>
#include <cstdlib>
srand(static_cast<unsigned>(time(0)));
eller
srand (time(NULL));
int var = rand()%maxrange +1;//från 1 till maxrange

```

Arrayer
-----
```
Bas:
Dice d1;//Objekt av typen Dice
Dice* d = nullptr;//Pekare av typen Dice

Statiskt:
Dice d[count] = {nullptr};//Statiskt alloerad array av Dice objekt
Dice* d[count] = {nullptr};//Statiskt allokerad array av Dice pekare
Dynamiskt:

Dice *d = new Dice[count];//Dynamiskt allokerad array av Dice objekt
Dice* *d = new Dice*[count];//Dynamiskt allokerad array av Dice pekare
```

Copiering
-----
#####Tilldelningsoperator
----
```
Typ& operator=(const Typ &origObj);
```
###Copy-konstruktor
----
#####Med dynamic cast
----
Superklass:
```
SuperKlass::SuperKlass(const SuperKlass &origObj) {
  this->capacity = origObj.capacity;
  this->antal = origObj.antal;
  this->TypeList = new Type*[origObj.capacity];
  
  TypeA* aTypeAPtr = nullptr;
  TypeB* aTypeBPtr = nullptr;

  for (int i = 0; i < origObj.antal; i++) {
    aTypeAPtr = dynamic_cast<TypeA*>(origObj.TypeList[i]);
    if (aTypeAPtr != nullptr) {//Det är ett TypeA objekt som ska skapas
      this->TypeList[i] = new TypeA(*aTypeAPtr);
    }
    else {
      aTypeBtr = dynamic_cast<TypeB*>(origObj.TypeList[i]);
      if (aTypeBPtr != nullptr) {
        this->persons[i] = new Employee(*aTypeBPtr);
      }
    }
  }
}
 ```
Subklass: 
I subklasserna ska det bara ha vanliga copy-konstruktorer
#####Med clone
----
Superklass:
```
virtual SuperTyp* clone()const = 0;

SuperKlass::SuperKlass(const SuperKlass &origObj) {
  this->capacity = origObj.capacity;
  this->antal = origObj.antal;
  this->TypeList = new Type*[origObj.capacity];
  for (int i = 0; i < origObj.antal; i++) {
    this->TypeList[i] = origObj.TypeList[i]->clone();
  }
}
```
Subklass:
```
Typ* clone()const;

*Typ clone()const {
	return new Typ(*this);//Kräver fungerande copy-konstruktor
}
```