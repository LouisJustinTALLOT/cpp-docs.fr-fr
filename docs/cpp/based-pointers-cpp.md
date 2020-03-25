---
title: Pointeurs basés sur (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: f16e9f6582ae846c0c19fc1dcbd86f09baba713e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181393"
---
# <a name="based-pointers-c"></a>Pointeurs basés sur (C++)

Le mot clé **__based** vous permet de déclarer des pointeurs basés sur des pointeurs (pointeurs qui sont des décalages par rapport à des pointeurs existants). Le mot clé **__based** est spécifique à Microsoft.

## <a name="syntax"></a>Syntaxe

```
type __based( base ) declarator
```

## <a name="remarks"></a>Notes

Les pointeurs basés sur des adresses de pointeur sont la seule forme du mot clé **__based** valide dans les compilations 32 bits ou 64 bits. Pour le compilateur Microsoft C/C++ 32 bits, un pointeur based est un décalage de 32 bits par rapport à une base de pointeur 32 bits. Une restriction similaire s'applique pour les environnements 64 bits, où un pointeur based est un décalage de 64 bits par rapport à la base 64 bits.

Les pointeurs basés sur pointeurs peuvent par exemple être utilisés pour des identificateurs persistants qui contiennent des pointeurs. Une liste liée composée de pointeurs basés sur un pointeur peut être enregistrée sur le disque, puis rechargée dans un autre emplacement mémoire, et les pointeurs restent valides. Par exemple :

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

Le pointeur `vpBuffer` reçoit l'adresse de la mémoire allouée à un point ultérieur dans le programme. La liste liée est déplacée par rapport à la valeur de `vpBuffer`.

> [!NOTE]
>  Les identificateurs persistants contenant des pointeurs peuvent également être obtenus à l’aide de [fichiers mappés en mémoire](/windows/win32/Memory/file-mapping).

Lors du déréférencement d'un pointeur based, la base doit être spécifiée explicitement ou connue implicitement via la déclaration.

Pour la compatibilité avec les versions précédentes, **_based** est un synonyme de **__based** sauf si l’option de compilateur [/za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

Le code suivant illustre comment modifier un pointeur based en modifiant sa base.

```cpp
// based_pointers2.cpp
// compile with: /EHsc
#include <iostream>

int a1[] = { 1,2,3 };
int a2[] = { 10,11,12 };
int *pBased;

typedef int __based(pBased) * pBasedPtr;

using namespace std;
int main() {
   pBased = &a1[0];
   pBasedPtr pb = 0;

   cout << *pb << endl;
   cout << *(pb+1) << endl;

   pBased = &a2[0];

   cout << *pb << endl;
   cout << *(pb+1) << endl;
}
```

```Output
1
2
10
11
```

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)
