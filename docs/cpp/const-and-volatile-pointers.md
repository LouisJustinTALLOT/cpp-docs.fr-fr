---
description: 'En savoir plus sur : les pointeurs const et volatile'
title: Pointeurs const et volatile
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: 142c6b83c242af969c5f6e1494a56e9598cf537d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344677"
---
# <a name="const-and-volatile-pointers"></a>Pointeurs const et volatile

Les mots clés [const](const-cpp.md) et [volatile](volatile-cpp.md) modifient la façon dont les pointeurs sont traités. Le **`const`** mot clé spécifie que le pointeur ne peut pas être modifié après l’initialisation ; par la suite, le pointeur est protégé contre les modifications.

Le **`volatile`** mot clé spécifie que la valeur associée au nom qui suit peut être modifiée par des actions autres que celles de l’application utilisateur. Par conséquent, le **`volatile`** mot clé est utile pour déclarer des objets dans la mémoire partagée qui sont accessibles par plusieurs processus ou zones de données globales utilisés pour la communication avec les routines de service d’interruption.

Lorsqu’un nom est déclaré comme **`volatile`** , le compilateur recharge la valeur à partir de la mémoire chaque fois que le programme y accède. Cela réduit considérablement les optimisations possibles. Toutefois, lorsque l'état d'un objet peut changer de manière inattendue, c'est la seule façon de garantir des performances prévisibles du programme.

Pour déclarer l’objet pointé par le pointeur en tant que **`const`** ou **`volatile`** , utilisez une déclaration de la forme suivante :

```cpp
const char *cpch;
volatile char *vpch;
```

Pour déclarer la valeur du pointeur, c’est-à-dire l’adresse réelle stockée dans le pointeur, en tant que **`const`** ou **`volatile`** , utilisez une déclaration de la forme suivante :

```cpp
char * const pchc;
char * volatile pchv;
```

Le langage C++ empêche les assignations qui autorisent la modification d’un objet ou d’un pointeur déclaré comme **`const`** . De telles assignations supprimeraient les informations avec lesquelles l'objet ou le pointeur a été déclaré, ce qui entraînerait la violation de l'objectif de la déclaration d'origine. Prenons les déclarations suivantes :

```cpp
const char cch = 'A';
char ch = 'B';
```

Étant donné les déclarations précédentes de deux objets ( `cch` , de type **const char** et `ch` , de type **Char)**, les déclarations/initialisations suivantes sont valides :

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

Les déclarations/initialisations suivantes sont erronées.

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

La déclaration de `pch2` déclare un pointeur par l'intermédiaire duquel un objet constant peut être modifié et par conséquent désactivé. La déclaration de `pch3` spécifie que le pointeur est constant, et non l’objet ; la déclaration n’est pas autorisée pour la même raison que la `pch2` déclaration n’est pas autorisée.

Les huit assignations suivantes indiquent l'assignation par l'intermédiaire du pointeur et la modification de la valeur du pointeur pour les déclarations précédentes ; pour le moment, supposons que l'initialisation est correcte de `pch1` à `pch8`.

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

Les pointeurs déclarés comme **`volatile`** , ou comme mélange de **`const`** et **`volatile`** , obéissent aux mêmes règles.

Les pointeurs vers **`const`** des objets sont souvent utilisés dans les déclarations de fonction comme suit :

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

L’instruction précédente déclare une fonction, [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), où deux des trois arguments sont de type pointeur vers **`char`** . Étant donné que les arguments sont passés par référence et non par valeur, la fonction serait libre de modifier à la fois `strDestination` et `strSource` si `strSource` n’a pas été déclaré comme **`const`** . La déclaration de `strSource` comme **`const`** garantit à l’appelant qu’il `strSource` ne peut pas être modifié par la fonction appelée.

> [!NOTE]
> Comme il existe une conversion standard de *TypeName* <strong>\*</strong> en **`const`** *TypeName* <strong>\*</strong> , il est légal de passer un argument de type `char *` à [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Toutefois, l’inverse n’est pas vrai ; Il n’existe pas de conversion implicite pour supprimer l' **`const`** attribut d’un objet ou d’un pointeur.

Un **`const`** pointeur d’un type donné peut être assigné à un pointeur du même type. Toutefois, il n’est pas possible **`const`** d’assigner un pointeur qui ne peut pas être assigné à un **`const`** pointeur. L'exemple de code suivant montre des assignations correctes et incorrectes :

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

L'exemple suivant montre comment déclarer un objet comme const si vous avez un pointeur désignant un pointeur vers un objet.

```cpp
// const_pointer2.cpp
struct X {
   X(int i) : m_i(i) { }
   int m_i;
};

int main() {
   // correct
   const X cx(10);
   const X * pcx = &cx;
   const X ** ppcx = &pcx;

   // also correct
   X const cx2(20);
   X const * pcx2 = &cx2;
   X const ** ppcx2 = &pcx2;
}
```

## <a name="see-also"></a>Voir aussi

[Pointeurs](pointers-cpp.md) 
 [Pointeurs bruts](raw-pointers.md)
