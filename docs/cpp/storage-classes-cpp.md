---
title: Classes de stockage (C++)
description: Dans le C, les mots clés statiques, extern et thread_local spécifient la durée de vie, le lien et l’emplacement de la mémoire d’une variable ou d’une fonction.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: 75ccb11689b4863d2d0df5edd6d066be6bd3858c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365344"
---
# <a name="storage-classes"></a>Classes de stockage

Une *classe de stockage* dans le cadre des déclarations variables de C est un spécificateur de type qui régit la durée de vie, le lien et l’emplacement de la mémoire des objets. Un objet donné ne peut avoir qu'une seule classe de stockage. Les variables définies dans un bloc ont un stockage automatique à moins qu’elles ne soient spécifiées autrement à l’aide **de l’arrière,** **statique,** ou **thread_local** spécificateurs. Les objets automatiques et les variables n'ont aucune liaison ; ils ne sont pas visibles pour le code en dehors du bloc. La mémoire leur est attribuée automatiquement lorsque l’exécution entre dans le bloc et a été désétributée lorsque le bloc est sorti.

**Remarques**

1. Le mot clé [mutable](../cpp/mutable-data-members-cpp.md) peut être considéré comme un spécificateur de classe de stockage. Toutefois, il est uniquement disponible dans la liste des membres d'une définition de classe.

1. **Visual Studio 2010 et plus tard:** Le mot clé **automatique** n’est plus un spécificateur de classe de stockage CMD, et le mot clé du **registre** est déprécié. **Visual Studio 2017 version 15.7 et plus tard:** (disponible avec [/std:c '17](../build/reference/std-specify-language-standard-version.md)) ) ) : Le mot clé du **registre** est supprimé de la langue C.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a>Statique

Le mot clé **statique** peut être utilisé pour déclarer les variables et les fonctions à portée globale, la portée de l’espace de nom et la portée de la classe. Les variables statiques peuvent également être déclarées dans la portée locale.

La durée statique signifie que l'objet ou la variable est alloué au démarrage du programme et est libéré à la fin de l'exécution du programme. La liaison externe signifie que le nom de la variable est visible de l'extérieur du fichier dans lequel la variable est déclarée. Inversement, une liaison interne signifie que le nom n'est pas visible hors du fichier dans lequel la variable est déclarée. Par défaut, un objet ou une variable défini dans l'espace de noms global a une durée statique et une liaison externe. Le mot clé **statique** peut être utilisé dans les situations suivantes.

1. Lorsque vous déclarez une variable ou une fonction à portée de fichier (portée globale et/ou namespace), le mot clé **statique** spécifie que la variable ou la fonction a un lien interne. Lorsque vous déclarez une variable, la variable a une durée statique et le compilateur l'initialise à 0, sauf si vous spécifiez une autre valeur.

1. Lorsque vous déclarez une variable dans une fonction, le mot clé **statique** précise que la variable conserve son état entre les appels à cette fonction.

1. Lorsque vous déclarez un membre de la donnée dans une déclaration de classe, le mot clé **statique** précise qu’une copie du membre est partagée par tous les cas de la classe. Des données membres statiques doivent être définies au niveau de la portée du fichier. Un membre de données intégral que vous déclarez comme **const statique** peut avoir un initialisateur.

1. Lorsque vous déclarez une fonction de membre dans une déclaration de classe, le mot clé **statique** précise que la fonction est partagée par tous les cas de la classe. Une fonction de membre statique ne peut pas accéder à un membre d’instance parce que la fonction n’a pas un **pointeur** implicite. Pour accéder à un membre d'instance, déclarez la fonction avec un paramètre qui est un pointeur ou une référence d'instance.

1. Vous ne pouvez pas déclarer les membres d'une union comme static. Cependant, une union anonyme déclarée à l’échelle mondiale doit être explicitement **déclarée statique**.

Cet exemple montre comment une variable **déclarée statique** dans une fonction conserve son état entre les appels à cette fonction.

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

Cet exemple montre l’utilisation de **statique** dans une classe.

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

Cet exemple montre une variable locale **déclarée statique** dans une fonction de membre. La variable statique est disponible pour la totalité du programme. Toutes les instances du type partagent la même copie de la variable statique.

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

À partir de C++11, une initialisation de variable locale statique est garantie comme étant thread-safe. Cette fonctionnalité est parfois appelée *statique magique*. Toutefois, dans une application multithread, toutes les assignations suivantes doivent être synchronisées. La fonction d’initialisation statique sans fil peut être désactivée en utilisant le drapeau [/Zc:threadSafeInit pour](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) éviter de prendre une dépendance à la CRT.

## <a name="extern"></a><a name="extern"></a>Extern

Les objets et les variables déclarés **extern déclarent** un objet qui est défini dans une autre unité de traduction ou dans une portée d’enceinte comme ayant un lien externe. Pour plus d’informations, voir les unités [d’extern](extern-cpp.md) et [de traduction et le lien](program-and-linkage-cpp.md).

## <a name="thread_local-c11"></a><a name="thread_local"></a>thread_local (C 11)

Une variable déclarée avec le **spécificateur thread_local** n’est accessible que sur le fil sur lequel il est créé. La variable est créée quand le thread est créé et détruite quand le thread est détruit. Chaque thread possède sa propre copie de la variable. Sur Windows, **thread_local** est fonctionnellement équivalent à l’attribut [Microsoft-spécifique __declspec( thread)](../cpp/thread.md) .

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

Choses à noter sur le spécificateur **thread_local:**

- Les variables dynamiquement parasumées de thread-local dans les DLL peuvent ne pas être correctement paraminées sur tous les threads d’appel. Pour plus d’informations, consultez [thread](thread.md).

- Le spécificateur **thread_local** peut être combiné avec **statique** ou **extern.**

- Vous ne pouvez appliquer **thread_local** qu’aux déclarations et définitions des données; **thread_local** ne peut pas être utilisé sur les déclarations ou définitions des fonctions.

- Vous pouvez spécifier **thread_local** uniquement sur les éléments de données avec une durée de stockage statique. Cela comprend les objets de données globaux **(statiques** et **externes),** les objets statiques locaux et les membres de données statiques des classes. Toute variable locale déclarée **thread_local** est implicitement statique si aucune autre classe de stockage n’est fournie; en d’autres termes, à périmètre `thread_local static` **thread_local** équivaut à .

- Vous devez spécifier **thread_local** à la fois pour la déclaration et la définition d’un objet local thread, que la déclaration et la définition se produisent dans le même fichier ou des fichiers distincts.

Sur Windows, **thread_local** est fonctionnellement équivalent à [__declspec(thread)](../cpp/thread.md) sauf que **__declspec(thread)** peut être appliqué à une définition de type et est valide dans le code C. Dans la mesure du possible, utilisez **thread_local** parce qu’il fait partie de la norme C et est donc plus portable.

## <a name="register"></a><a name="register"></a>Registre

**Visual Studio 2017 version 15.3 et plus tard** (disponible avec [/std:c '17](../build/reference/std-specify-language-standard-version.md)): Le mot clé **du registre** n’est plus une classe de stockage pris en charge. Le mot clé est toujours réservé dans la norme pour une utilisation future.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Exemple : initialisation automatique vs statique

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

Cet exemple montre comment et `I1` `I2`quand `I3` les objets, , et sont parasécés et quand ils sont détruits.

Il y a plusieurs points à noter au sujet du programme :

- D'abord, `I1` et `I2` sont automatiquement détruits lorsque l'ordre d'exécution quitte le bloc dans lequel ils sont définis.

- Ensuite, en C++, il n'est pas nécessaire de déclarer des objets ou des variables au début d'un bloc. En outre, ces objets sont initialisés uniquement lorsque l'ordre d'exécution atteint leurs définitions. `I2` (et `I3` sont des exemples de telles définitions.) La sortie montre exactement quand ils sont parasés.

- Enfin, les variables locales statiques telles que `I3` conservent leurs valeurs pour la durée du programme, mais sont détruites à la fin du programme.

## <a name="see-also"></a>Voir aussi

[Déclarations et définitions](../cpp/declarations-and-definitions-cpp.md)
