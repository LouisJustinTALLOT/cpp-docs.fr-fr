---
title: Alias et typedefs (C++)
ms.date: 11/04/2016
f1_keywords:
- typedef_cpp
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
ms.openlocfilehash: 155f1868123514dfec89ab448ef22f2da225c4d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155288"
---
# <a name="aliases-and-typedefs-c"></a>Alias et typedefs (C++)

Vous pouvez utiliser un *déclaration d’alias* pour déclarer un nom à utiliser comme un synonyme pour un type déclaré précédemment. (Ce mécanisme est également appelé de manière informelle un *alias de type*). Vous pouvez également utiliser ce mécanisme pour créer un *modèle d’alias*, qui peut être particulièrement utile pour les allocateurs personnalisés.

## <a name="syntax"></a>Syntaxe

```
using identifier = type;
```

## <a name="remarks"></a>Notes

*identifier*<br/>
Nom de l'alias.

*type*<br/>
Identificateur de type pour lequel vous créez un alias.

Un alias n'introduit pas de nouveau type et ne peut pas modifier la signification du nom d'un type existant.

La forme la plus simple d’un alias est équivalente à la **typedef** mécanisme de C ++ 03 :

```cpp
// C++11
using counter = long;

// C++03 equivalent:
// typedef long counter;
```

Tous deux permettent de créer des variables de type « counter ». Un élément plus utile est un alias de type comme celui-ci pour `std::ios_base::fmtflags` :

```cpp
// C++11
using fmtfl = std::ios_base::fmtflags;

// C++03 equivalent:
// typedef std::ios_base::fmtflags fmtfl;

fmtfl fl_orig = std::cout.flags();
fmtfl fl_hex = (fl_orig & ~std::cout.basefield) | std::cout.showbase | std::cout.hex;
// ...
std::cout.flags(fl_hex);
```

Alias également travailler avec des pointeurs de fonction, mais sont beaucoup plus lisibles que le typedef équivalent :

```cpp
// C++11
using func = void(*)(int);

// C++03 equivalent:
// typedef void (*func)(int);

// func can be assigned to a function pointer value
void actual_function(int arg) { /* some code */ }
func fptr = &actual_function;
```

Une limitation de la **typedef** mécanisme est qu’il ne fonctionne pas avec les modèles. Toutefois, la syntaxe de l'alias de type en C++11 permet la création de modèles d'alias :

```cpp
template<typename T> using ptr = T*;

// the name 'ptr<T>' is now an alias for pointer to T
ptr<int> ptr_int;
```

## <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser un modèle d'alias avec un allocateur personnalisé, dans ce cas un type de vecteur entier. Vous pouvez remplacer n’importe quel type de **int** pour créer un alias pratique pour masquer le paramètre complex répertorie dans votre code fonctionnel principal. En utilisant l'allocateur personnalisé dans votre code, vous pouvez améliorer la lisibilité et réduire le risque d'introduire des bogues causés par les fautes de frappe.

```cpp
#include <stdlib.h>
#include <new>

template <typename T> struct MyAlloc {
    typedef T value_type;

    MyAlloc() { }
    template <typename U> MyAlloc(const MyAlloc<U>&) { }

    bool operator==(const MyAlloc&) const { return true; }
    bool operator!=(const MyAlloc&) const { return false; }

    T * allocate(const size_t n) const {
        if (n == 0) {
            return nullptr;
        }

        if (n > static_cast<size_t>(-1) / sizeof(T)) {
            throw std::bad_array_new_length();
        }

        void * const pv = malloc(n * sizeof(T));

        if (!pv) {
            throw std::bad_alloc();
        }

        return static_cast<T *>(pv);
    }

    void deallocate(T * const p, size_t) const {
        free(p);
    }
};

#include <vector>
using MyIntVector = std::vector<int, MyAlloc<int>>;

#include <iostream>

int main ()
{
    MyIntVector foov = { 1701, 1764, 1664 };

    for (auto a: foov) std::cout << a << " ";
    std::cout << "\n";

    return 0;
}
```

```Output
1701 1764 1664
```

## <a name="typedefs"></a>Typedef

Un **typedef** déclaration introduit un nom qui, dans sa portée, devient un synonyme du type donné par le *déclaration de type* partie de la déclaration.

Vous pouvez utiliser des déclarations typedef pour construire des noms plus courts ou plus explicites pour des types déjà définis par le langage ou pour des types que vous avez déclarés. Les noms typedef vous permettent d'encapsuler des détails d'implémentation susceptibles de changer.

Contrairement à la **classe**, **struct**, **union**, et **enum** déclarations, **typedef** n’introduisent pas de nouveaux types, ils introduisent de nouveaux noms pour des types existants.

Les noms déclarés à l’aide de **typedef** occupent le même espace de noms que d’autres identificateurs (sauf les étiquettes d’instruction). Par conséquent, ils ne peuvent pas utiliser le même identificateur qu'un nom déclaré précédemment, sauf dans une déclaration de type classe. Prenons l'exemple suivant :

```cpp
// typedef_names1.cpp
// C2377 expected
typedef unsigned long UL;   // Declare a typedef name, UL.
int UL;                     // C2377: redefined.
```

Les règles de masquage de nom qui se rapportent à d’autres identificateurs régissent également la visibilité des noms déclarés à l’aide de **typedef**. Par conséquent, l'exemple suivant est autorisé en C++ :

```cpp
// typedef_names2.cpp
typedef unsigned long UL;   // Declare a typedef name, UL
int main()
{
   unsigned int UL;   // Redeclaration hides typedef name
}

// typedef UL back in scope
```

```cpp
// typedef_specifier1.cpp
typedef char FlagType;

int main()
{
}

void myproc( int )
{
    int FlagType;
}
```

Lors de la déclaration d'un identificateur de portée locale du même nom qu'un typedef, ou lors de la déclaration d'un membre d'une structure ou d'une union dans la même portée ou dans une portée interne, le spécificateur de type doit être spécifié. Exemple :

```cpp
typedef char FlagType;
const FlagType x;
```

Pour réutiliser le nom `FlagType` pour un identificateur, un membre de structure ou un membre d'union, le type doit être fourni :

```cpp
const int FlagType;  // Type specifier required
```

Il ne suffit pas de dire

```cpp
const FlagType;      // Incomplete specification
```

car `FlagType` est considéré comme faisant partie du type, et non comme un identificateur qui est redéclaré. Cette déclaration est considérée comme étant une déclaration non conforme comme

```cpp
int;  // Illegal declaration
```

Vous pouvez déclarer tout type avec typedef, y compris des types pointeur, fonction et tableau. Vous pouvez déclarer un nom typedef pour un pointeur vers une structure ou un type union avant de définir la structure ou le type union, tant que la définition a la même visibilité que la déclaration.

### <a name="examples"></a>Exemples

Une des utilisations de **typedef** déclarations consiste à rendre les déclarations plus uniformes et compactes. Exemple :

```cpp
typedef char CHAR;          // Character type.
typedef CHAR * PSTR;        // Pointer to a string (char *).
PSTR strchr( PSTR source, CHAR target );
typedef unsigned long ulong;
ulong ul;     // Equivalent to "unsigned long ul;"
```

Pour utiliser **typedef** pour spécifier les types fondamentaux et dérivés dans la même déclaration, séparez les déclarateurs par des virgules. Exemple :

```cpp
typedef char CHAR, *PSTR;
```

L’exemple suivant fournit le type `DRAWF` pour une fonction qui ne retourne aucune valeur et qui accepte deux arguments int :

```cpp
typedef void DRAWF( int, int );
```

Après la méthode ci-dessus **typedef** instruction, la déclaration

```cpp
DRAWF box;
```

équivaut à la déclaration

```cpp
void box( int, int );
```

**typedef** est souvent associée à **struct** pour déclarer et nommer les types définis par l’utilisateur :

```cpp
// typedef_specifier2.cpp
#include <stdio.h>

typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;

int main()
{
    mystruct ms;
    ms.i = 10;
    ms.f = 0.99;
    printf_s("%d   %f\n", ms.i, ms.f);
}
```

```Output
10   0.990000
```

### <a name="re-declaration-of-typedefs"></a>Redéclaration de typedefs

Le **typedef** déclaration peut être utilisée pour redéclarer le même nom pour faire référence au même type. Exemple :

```cpp
// FILE1.H
typedef char CHAR;

// FILE2.H
typedef char CHAR;

// PROG.CPP
#include "file1.h"
#include "file2.h"   // OK
```

Le programme *PROG. CPP* inclut deux fichiers d’en-tête, et contiennent des **typedef** déclarations pour le nom `CHAR`. Tant que les deux déclarations désignent le même type, cette redéclaration est acceptable.

Un **typedef** ne peut pas redéfinir un nom qui a précédemment été déclaré comme un type différent. Par conséquent, si *Fichier2. H* contient

```cpp
// FILE2.H
typedef int CHAR;     // Error
```

le compilateur fournit une erreur en raison de la tentative de redéclaration du nom `CHAR` pour faire référence à un type différent. Cela s'étend aux constructions telles que :

```cpp
typedef char CHAR;
typedef CHAR CHAR;      // OK: redeclared as same type

typedef union REGS      // OK: name REGS redeclared
{                       //  by typedef name with the
    struct wordregs x;  //  same meaning.
    struct byteregs h;
} REGS;
```

### <a name="typedefs-in-c-vs-c"></a>typedefs en C++ et C

Utiliser le **typedef** spécificateur avec les types de classe est pris en charge principalement en raison de la pratique C ANSI de la déclaration des structures sans nom dans **typedef** déclarations. Par exemple, de nombreux programmeurs en langage C utilisent ce qui suit :

```cpp
// typedef_with_class_types1.cpp
// compile with: /c
typedef struct {   // Declare an unnamed structure and give it the
                   // typedef name POINT.
   unsigned x;
   unsigned y;
} POINT;
```

L'avantage de ce type de déclaration est qu'il permet des déclarations telles que :

```cpp
POINT ptOrigin;
```

plutôt que :

```cpp
struct point_t ptOrigin;
```

En C++, la différence entre **typedef** noms et les types réels (déclarés avec le **classe**, **struct**, **union**et **enum** mots clés) est plus distincte. Bien que la pratique C consistant à déclarer une structure sans nom dans un **typedef** instruction fonctionne toujours, il ne présente aucun avantage codifié comme il le fait en C.

```cpp
// typedef_with_class_types2.cpp
// compile with: /c /W1
typedef struct {
   int POINT();
   unsigned x;
   unsigned y;
} POINT;
```

L’exemple précédent déclare une classe nommée `POINT` à l’aide de la classe sans nom **typedef** syntaxe. `POINT` est considérée comme un nom de classe. Toutefois, les restrictions suivantes s'appliquent aux noms introduits de cette façon :

- Le nom (synonyme) ne peut pas apparaître après un **classe**, **struct**, ou **union** préfixe.

- Le nom ne peut pas être utilisé en tant que nom de constructeur ou de destructeur dans une déclaration de classe.

En résumé, cette syntaxe ne fournit pas de mécanisme pour l'héritage, la construction ou la destruction.