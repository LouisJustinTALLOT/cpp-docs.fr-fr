---
title: Classes de stockage (C++)
description: En C++, les mots clés static, extern et thread_local spécifient la durée de vie, la liaison et l’emplacement de mémoire d’une variable ou d’une fonction.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: c3fc87980d1fd0af5b803a8e590855f6429c847e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213162"
---
# <a name="storage-classes"></a>Classes de stockage

Une *classe de stockage* dans le contexte des déclarations de variables C++ est un spécificateur de type qui régit la durée de vie, la liaison et l’emplacement de mémoire des objets. Un objet donné ne peut avoir qu'une seule classe de stockage. Les variables définies dans un bloc ont un stockage automatique, sauf spécification contraire à l’aide des **`extern`** **`static`** **`thread_local`** spécificateurs, ou. Les objets automatiques et les variables n'ont aucune liaison ; ils ne sont pas visibles pour le code en dehors du bloc. La mémoire est allouée automatiquement quand l’exécution entre dans le bloc et désallouée lors de la sortie du bloc.

**Notes**

1. Le mot clé [mutable](../cpp/mutable-data-members-cpp.md) peut être considéré comme un spécificateur de classe de stockage. Toutefois, il est uniquement disponible dans la liste des membres d'une définition de classe.

1. **Visual Studio 2010 et versions ultérieures :** Le **`auto`** mot clé n’est plus un spécificateur de classe de stockage C++ et le **`register`** mot clé est déconseillé. **Visual Studio 2017 version 15,7 et versions ultérieures :** (disponible avec [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ) : le **`register`** mot clé est supprimé du langage C++.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a> `static`

Le **`static`** mot clé peut être utilisé pour déclarer des variables et des fonctions au niveau de la portée globale, de la portée espace de noms et de la portée de la classe. Les variables statiques peuvent également être déclarées dans la portée locale.

La durée statique signifie que l'objet ou la variable est alloué au démarrage du programme et est libéré à la fin de l'exécution du programme. La liaison externe signifie que le nom de la variable est visible de l'extérieur du fichier dans lequel la variable est déclarée. Inversement, une liaison interne signifie que le nom n'est pas visible hors du fichier dans lequel la variable est déclarée. Par défaut, un objet ou une variable défini dans l'espace de noms global a une durée statique et une liaison externe. Le **`static`** mot clé peut être utilisé dans les situations suivantes.

1. Quand vous déclarez une variable ou une fonction au niveau de la portée du fichier (portée globale et/ou portée de l’espace de noms), le **`static`** mot clé spécifie que la variable ou la fonction a une liaison interne. Lorsque vous déclarez une variable, la variable a une durée statique et le compilateur l'initialise à 0, sauf si vous spécifiez une autre valeur.

1. Quand vous déclarez une variable dans une fonction, le **`static`** mot clé spécifie que la variable conserve son état entre les appels à cette fonction.

1. Quand vous déclarez un membre de données dans une déclaration de classe, le **`static`** mot clé spécifie qu’une copie du membre est partagée par toutes les instances de la classe. Des données membres statiques doivent être définies au niveau de la portée du fichier. Une donnée membre intégrale que vous déclarez comme **`const static`** peut avoir un initialiseur.

1. Quand vous déclarez une fonction membre dans une déclaration de classe, le **`static`** mot clé spécifie que la fonction est partagée par toutes les instances de la classe. Une fonction membre statique ne peut pas accéder à un membre d’instance car la fonction n’a pas de pointeur implicite **`this`** . Pour accéder à un membre d'instance, déclarez la fonction avec un paramètre qui est un pointeur ou une référence d'instance.

1. Vous ne pouvez pas déclarer les membres d'une union comme static. Toutefois, une Union anonyme globalement déclarée doit être déclarée explicitement **`static`** .

Cet exemple montre comment une variable déclarée **`static`** dans une fonction conserve son état entre les appels à cette fonction.

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

Cet exemple illustre l’utilisation de **`static`** dans une classe.

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

Cet exemple montre une variable locale déclarée **`static`** dans une fonction membre. La **`static`** variable est disponible pour l’ensemble du programme ; toutes les instances du type partagent la même copie de la **`static`** variable.

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

À partir de C++ 11, **`static`** l’initialisation d’une variable locale est garantie comme étant thread-safe. Cette fonctionnalité est parfois appelée « *statiques magiques*». Toutefois, dans une application multithread, toutes les assignations suivantes doivent être synchronisées. La fonctionnalité d’initialisation statique thread-safe peut être désactivée à l’aide de l' [`/Zc:threadSafeInit-`](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) indicateur afin d’éviter de dépendre de la bibliothèque CRT.

## <a name="extern"></a><a name="extern"></a> `extern`

Les objets et les variables déclarés comme **`extern`** déclarent un objet défini dans une autre unité de traduction ou dans une portée englobante comme ayant une liaison externe. Pour plus d’informations, consultez [`extern`](extern-cpp.md) et les [unités de traduction et la liaison](program-and-linkage-cpp.md).

## <a name="thread_local-c11"></a><a name="thread_local"></a>`thread_local`(C++ 11)

Une variable déclarée avec le **`thread_local`** spécificateur est accessible uniquement sur le thread sur lequel elle est créée. La variable est créée quand le thread est créé et détruite quand le thread est détruit. Chaque thread possède sa propre copie de la variable. Sur Windows, **`thread_local`** est fonctionnellement équivalent à l’attribut spécifique à Microsoft [`__declspec( thread )`](../cpp/thread.md) .

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

Points à noter concernant le **`thread_local`** spécificateur :

- Les variables locales de threads initialisées dynamiquement dans les dll peuvent ne pas être initialisées correctement sur tous les threads d’appel. Pour plus d’informations, consultez [`thread`](thread.md).

- Le **`thread_local`** spécificateur peut être combiné avec **`static`** ou **`extern`** .

- Vous pouvez appliquer **`thread_local`** uniquement aux déclarations et aux définitions de données ; **`thread_local`** ne peut pas être utilisé sur des définitions ou des déclarations de fonction.

- Vous pouvez spécifier **`thread_local`** uniquement sur les éléments de données ayant une durée de stockage statique. Cela comprend les objets de données globaux (à la fois **`static`** et **`extern`** ), les objets statiques locaux et les membres de données statiques des classes. Toute variable locale déclarée **`thread_local`** est implicitement statique si aucune autre classe de stockage n’est fournie ; en d’autres termes, la portée de bloc **`thread_local`** est équivalente à **`thread_local static`** .

- Vous devez spécifier **`thread_local`** à la fois pour la déclaration et la définition d’un objet local de thread, si la déclaration et la définition se produisent dans le même fichier ou dans des fichiers distincts.

Sous Windows, **`thread_local`** est fonctionnellement équivalent à [`__declspec(thread)`](../cpp/thread.md) , sauf que *`*__declspec(thread)`* * peut être appliqué à une définition de type et est valide dans le code C. Si possible, utilisez **`thread_local`** car il fait partie de la norme C++ et est donc plus portable.

## <a name="register"></a><a name="register"></a>annuler

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ) : le **`register`** mot clé n’est plus une classe de stockage prise en charge. Le mot clé est toujours réservé dans le standard pour une utilisation ultérieure.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Exemple : initialisation automatique et initialisation statique

Une variable automatique ou un objet local est initialisé chaque fois que l'ordre d'exécution atteint sa définition. Une variable automatique ou un objet statique est initialisé la première fois que l'ordre d'exécution atteint sa définition.

Prenons l'exemple suivant, qui définit une classe qui stocke l'initialisation et la destruction des objets, puis définit trois objets, `I1`, `I2`, et `I3`:

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

Cet exemple montre comment et quand les objets `I1` , `I2` , et `I3` sont initialisés et quand ils sont détruits.

Il y a plusieurs points à noter sur le programme :

- D'abord, `I1` et `I2` sont automatiquement détruits lorsque l'ordre d'exécution quitte le bloc dans lequel ils sont définis.

- Ensuite, en C++, il n'est pas nécessaire de déclarer des objets ou des variables au début d'un bloc. En outre, ces objets sont initialisés uniquement lorsque l'ordre d'exécution atteint leurs définitions. ( `I2` et `I3` sont des exemples de ces définitions.) La sortie indique exactement quand elles sont initialisées.

- Enfin, les variables locales statiques telles que `I3` conservent leurs valeurs pour la durée du programme, mais sont détruites à la fin du programme.

## <a name="see-also"></a>Voir aussi

[Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)
