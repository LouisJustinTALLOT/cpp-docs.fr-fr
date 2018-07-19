---
title: Classes de stockage (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
- register_cpp
dev_langs:
- C++
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f89651ba671bf66d7d27edb047db6d1b6b15ee06
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940922"
---
# <a name="storage-classes-c"></a>Classes de stockage (C++)  
  
Un *classe de stockage* dans le contexte de C++, déclarations de variable est un spécificateur de type qui régit l’emplacement de mémoire, la liaison et la durée de vie des objets. Un objet donné ne peut avoir qu'une seule classe de stockage. Les variables définies dans un bloc ont un stockage automatique, sauf indication contraire à l’aide de la **extern**, **statique**, ou `thread_local` spécificateurs. Les objets automatiques et les variables n'ont aucune liaison ; ils ne sont pas visibles pour le code en dehors du bloc.  
  
**Notes**  
  
1.  Le [mutable](../cpp/mutable-data-members-cpp.md) mot clé peut être considéré comme un spécificateur de classe de stockage. Toutefois, il est uniquement disponible dans la liste des membres d'une définition de classe.  
  
2.  **Visual C++ 2010 et versions ultérieures :** le **automatique** mot clé n’est plus un spécificateur de classe de stockage C++ et le **inscrire** mot clé est déconseillé. **Visual Studio 2017 version 15.7 et ultérieure :** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : le **inscrire** mot clé est supprimé du langage C++.


```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>Dans cette section :

- [static](#static)
- [extern](#extern)
- [thread_local](#thread_local)

## <a name="static"></a> Statique

Le **statique** mot clé peut être utilisé pour déclarer des variables et des fonctions dans la portée globale, de portée espace de noms et de portée de classe. Les variables statiques peuvent également être déclarées dans la portée locale.

La durée statique signifie que l'objet ou la variable est alloué au démarrage du programme et est libéré à la fin de l'exécution du programme. La liaison externe signifie que le nom de la variable est visible de l'extérieur du fichier dans lequel la variable est déclarée. Inversement, une liaison interne signifie que le nom n'est pas visible hors du fichier dans lequel la variable est déclarée. Par défaut, un objet ou une variable défini dans l'espace de noms global a une durée statique et une liaison externe. Le **statique** mot clé peut être utilisé dans les situations suivantes.

1. Lorsque vous déclarez une variable ou une fonction à la portée du fichier (globale et/ou portée espace de noms), le **statique** mot clé spécifie que la variable ou la fonction a une liaison interne. Lorsque vous déclarez une variable, la variable a une durée statique et le compilateur l'initialise à 0, sauf si vous spécifiez une autre valeur.

1. Lorsque vous déclarez une variable dans une fonction, le **statique** mot clé spécifie que la variable conserve son état entre les appels à cette fonction.

1. Lorsque vous déclarez un membre de données dans une déclaration de classe, le **statique** mot clé spécifie qu’une seule copie du membre est partagée par toutes les instances de la classe. Des données membres statiques doivent être définies au niveau de la portée du fichier. Une donnée membre intégrale que vous déclarez comme **static const** peut avoir un initialiseur.

1. Lorsque vous déclarez une fonction membre dans une déclaration de classe, le **statique** mot clé spécifie que la fonction est partagée par toutes les instances de la classe. Une fonction membre statique ne peut pas accéder à un membre d’instance, car la fonction n’a pas implicite **cela** pointeur. Pour accéder à un membre d'instance, déclarez la fonction avec un paramètre qui est un pointeur ou une référence d'instance.

1. Vous ne pouvez pas déclarer les membres d'une union comme static. Toutefois, une union anonyme globalement déclarée doit être déclarée explicitement **statique**.

Cet exemple montre comment une variable déclarée **statique** dans une fonction conserve son état entre les appels à cette fonction.

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

Cet exemple illustre l’utilisation de **statique** dans une classe.

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

Cet exemple montre une variable locale déclarée **statique** dans une fonction membre. La variable statique est disponible pour la totalité du programme. Toutes les instances du type partagent la même copie de la variable statique.

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

À partir de C++11, une initialisation de variable locale statique est garantie comme étant thread-safe. Cette fonctionnalité est parfois appelée *magic statiques*. Toutefois, dans une application multithread, toutes les assignations suivantes doivent être synchronisées. La fonctionnalité de l’initialisation statique de thread-safe peut être désactivée à l’aide de la [/Zc:threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) indicateur pour éviter une dépendance sur la bibliothèque CRT.

## <a name="extern"></a> extern

Objets et les variables déclarées en tant que **extern** déclarer un objet qui est défini dans une autre unité de traduction ou dans une portée englobante comme ayant une liaison externe.

Déclaration de **const** variables avec le **extern** classe de stockage force la variable à avoir une liaison externe. Une initialisation d’un **extern const** variable n’est autorisée dans l’unité de traduction de définition. Les initialisations dans des unités de traduction autres que l'unité de traduction de définition produisent des résultats indéterminés. Pour plus d’informations, consultez [utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)

Le [/Zc : externconstexpr](../build/reference/zc-externconstexpr.md) option du compilateur indique au compilateur d’appliquer [une liaison externe]() aux variables déclarées à l’aide de `extern constexpr`. Dans les versions antérieures de Visual Studio et, par défaut ou si **/Zc:externConstexpr-** est spécifié, Visual Studio applique une liaison interne à **constexpr** même si de variables le **extern** mot clé est utilisé. Le **/Zc : externconstexpr** option est disponible à partir de Visual Studio 2017 mise à jour 15.6. et est désactivée par défaut. La /permissive-option n’active pas/Zc : externconstexpr.

Le code suivant montre deux **extern** déclarations, `DefinedElsewhere` (qui fait référence à un nom défini dans une autre unité de traduction) et `DefinedHere` (qui fait référence à un nom défini dans une portée englobante) :

```cpp
// external.cpp
// DefinedElsewhere is defined in another translation unit
extern int DefinedElsewhere;   
int main() {
   int DefinedHere; 
   {
      // refers to DefinedHere in the enclosing scope
      extern int DefinedHere;
   }
}
```

## <a name="thread_local"></a> thread_local (C ++ 11)

Une variable déclarée avec le spécificateur `thread_local` est accessible uniquement sur le thread sur lequel elle est créée. La variable est créée quand le thread est créé et détruite quand le thread est détruit. Chaque thread possède sa propre copie de la variable. Sur Windows, `thread_local` est fonctionnellement équivalent à spécifique à Microsoft, [__declspec (thread)](../cpp/thread.md) attribut.

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

Choses à noter concernant le `thread_local` spécificateur :

- Les variables locales de thread dynamiquement initialisés dans les DLL ne peuvent pas être initialisés correctement sur tous les threads appelants. Pour plus d’informations, consultez [thread](thread.md).

-  Le `thread_local` spécificateur peut-être être combiné avec **statique** ou **extern**.

-  Vous pouvez appliquer `thread_local` uniquement aux déclarations de données et définitions ; `thread_local` ne peut pas être utilisé sur des définitions ou déclarations de fonction.

-  Vous pouvez spécifier `thread_local` uniquement sur les éléments de données ayant une durée de stockage statique. Cela inclut les objets de données globaux (à la fois **statique** et **extern**), les objets statiques locaux et les données membres statiques des classes. Toute variable locale déclarée `thread_local` est implicitement statique si aucune autre classe de stockage n’est fourni ; en d’autres termes, à la portée de bloc `thread_local` équivaut à `thread_local static`. 

-  Vous devez spécifier `thread_local` à la fois pour la déclaration et la définition d'un objet local de thread, que la déclaration et la définition se produisent dans le même fichier ou dans des fichiers séparés.

Sur Windows, `thread_local` est fonctionnellement équivalent à [__declspec (thread)](../cpp/thread.md) , à ceci près que `__declspec(thread)` peut être appliqué à une définition de type et n’est valide dans le code C. Si possible, utilisez `thread_local`, car il fait partie de la norme C++ et est par conséquent plus portable.

##  <a name="register"></a>  s’inscrire

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : le **inscrire** mot clé n’est plus une classe de stockage pris en charge. Le mot clé est toujours réservé dans la norme pour une utilisation ultérieure. 

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Exemple : les automatique et l’initialisation statique

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

Cet exemple montre comment et quand les objets `I1`, `I2`, et `I3` sont initialisés et quand ils sont détruits.

Il existe plusieurs points à noter concernant le programme :

- D'abord, `I1` et `I2` sont automatiquement détruits lorsque l'ordre d'exécution quitte le bloc dans lequel ils sont définis.

- Ensuite, en C++, il n'est pas nécessaire de déclarer des objets ou des variables au début d'un bloc. En outre, ces objets sont initialisés uniquement lorsque l'ordre d'exécution atteint leurs définitions. (`I2` et `I3` sont des exemples de telles définitions.) La sortie montre exactement quand ils sont initialisés.

- Enfin, les variables locales statiques telles que `I3` conservent leurs valeurs pour la durée du programme, mais sont détruites à la fin du programme.

## <a name="see-also"></a>Voir aussi

 [Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)
