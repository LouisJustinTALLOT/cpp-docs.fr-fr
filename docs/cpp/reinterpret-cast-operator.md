---
title: reinterpret_cast, opérateur
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 33da7427adeb0a0cade2a369664d7fbd34790681
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233598"
---
# <a name="reinterpret_cast-operator"></a>reinterpret_cast, opérateur

Autorise la conversion de tout pointeur en tout autre type pointeur. Autorise également la conversion de tout type entier en tout type pointeur et vice versa.

## <a name="syntax"></a>Syntaxe

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>Notes

Une utilisation incorrecte de l' **`reinterpret_cast`** opérateur peut facilement être dangereuse. À moins que la conversion souhaitée soit fondamentalement de bas niveau, vous devez utiliser l'un des autres opérateurs de cast.

L' **`reinterpret_cast`** opérateur peut être utilisé pour les conversions telles que **`char*`** to **`int*`** , `One_class*` ou to `Unrelated_class*` , qui sont fondamentalement dangereuses.

Le résultat d’un **`reinterpret_cast`** ne peut pas être utilisé en toute sécurité pour un autre type que celui d’origine. Les autres utilisations sont, au mieux, non portables.

L' **`reinterpret_cast`** opérateur ne peut pas effectuer un cast des **`const`** **`volatile`** attributs, ou **`__unaligned`** . Pour plus d’informations sur la suppression de ces attributs, consultez [Const_cast Operator](../cpp/const-cast-operator.md) .

L' **`reinterpret_cast`** opérateur convertit une valeur de pointeur null en valeur de pointeur null du type de destination.

Une utilisation pratique de **`reinterpret_cast`** est dans une fonction de hachage, qui mappe une valeur à un index de telle sorte que deux valeurs distinctes finissent rarement par le même index.

```cpp
#include <iostream>
using namespace std;

// Returns a hash code based on an address
unsigned short Hash( void *p ) {
   unsigned int val = reinterpret_cast<unsigned int>( p );
   return ( unsigned short )( val ^ (val >> 16));
}

using namespace std;
int main() {
   int a[20];
   for ( int i = 0; i < 20; i++ )
      cout << Hash( a + i ) << endl;
}

Output:
64641
64645
64889
64893
64881
64885
64873
64877
64865
64869
64857
64861
64849
64853
64841
64845
64833
64837
64825
64829
```

Le **`reinterpret_cast`** permet au pointeur d’être traité comme un type intégral. Le résultat binaire est alors déplacé et soumis à une opération XOR avec lui-même pour produire un index unique (à un niveau de probabilité élevé). L’index est ensuite tronqué par un cast de style C standard en type de retour de la fonction.

## <a name="see-also"></a>Voir aussi

[Opérateurs de cast](../cpp/casting-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
