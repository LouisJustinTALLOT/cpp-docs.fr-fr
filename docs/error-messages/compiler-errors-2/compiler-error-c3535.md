---
title: Erreur du compilateur C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 60ffd5d8decd5c9065ca55cfed34383278359f3e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228789"
---
# <a name="compiler-error-c3535"></a>Erreur du compilateur C3535

Impossible de déduire le type de’type1 'à partir de’type2 '

Le type de la variable déclarée par le **`auto`** mot clé ne peut pas être déduit du type de l’expression d’initialisation. Par exemple, cette erreur se produit si l’expression d’initialisation prend la valeur **`void`** , ce qui n’est pas un type.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Assurez-vous que le type de l’expression d’initialisation n’est pas **`void`** .

1. Vérifiez que la déclaration n’est pas un pointeur vers un type fondamental. Pour plus d’informations, consultez [types fondamentaux](../../cpp/fundamental-types-cpp.md).

1. Assurez-vous que si la déclaration est un pointeur vers un type, l’expression d’initialisation est un type pointeur.

## <a name="example"></a>Exemple

L’exemple suivant donne C3535 parce que l’expression d’initialisation prend la valeur **`void`** .

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>Exemple

L’exemple suivant donne C3535 parce que l’instruction déclare la variable `x` en tant que pointeur vers un type déduit, mais le type de l’expression d’initialiseur est double. Par conséquent, le compilateur ne peut pas déduire le type de la variable.

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>Exemple

L’exemple suivant donne C3535, car `p` la variable déclare un pointeur vers un type déduit, mais l’expression d’initialisation n’est pas un type pointeur.

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>Voir aussi

[Auto, mot clé](../../cpp/auto-keyword.md)<br/>
[Types fondamentaux](../../cpp/fundamental-types-cpp.md)
