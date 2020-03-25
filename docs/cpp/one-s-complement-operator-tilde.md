---
title: 'Opérateur&#39;de complément un s : ~'
ms.date: 11/04/2016
f1_keywords:
- "~"
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 777f253925caf38647863bdaa93fde8d5a03e3f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177714"
---
# <a name="one39s-complement-operator-"></a>Opérateur&#39;de complément un s : ~

## <a name="syntax"></a>Syntaxe

```
~ cast-expression
```

## <a name="remarks"></a>Notes

L’opérateur de complément à un (`~`), parfois appelé l’opérateur de complément de bits, génère un complément à un au niveau du bit de son opérande. Autrement dit, chaque bit qui est 1 dans l’opérande est 0 dans le résultat. Inversement, chaque bit qui est 0 dans l’opérande est 1 dans le résultat. L'opérande de l'opérateur de complément à un doit être un type intégral.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour ~

L’opérateur **compl (** est l’équivalent textuel de `~`. Il existe deux façons d’accéder à l’opérateur **compl (** dans vos programmes : incluez le fichier d’en-tête `iso646.h`ou compilez avec [/za](../build/reference/za-ze-disable-language-extensions.md).

## <a name="example"></a>Exemple

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

Dans cet exemple, la nouvelle valeur assignée à `y` est le complément à 1 de la valeur non signée 0xFFFF ou 0x0000.

La promotion intégrale est exécutée sur les opérandes intégraux et le type résultant est le type vers lequel l'opérande est promu. Pour plus d’informations sur la façon dont la promotion est effectuée, consultez [conversions standard](standard-conversions.md) .

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs arithmétiques unaires](../c-language/unary-arithmetic-operators.md)
