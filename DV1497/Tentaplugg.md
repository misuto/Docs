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