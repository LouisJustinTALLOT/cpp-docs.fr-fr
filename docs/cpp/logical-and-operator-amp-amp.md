---
title: 'Opérateur AND logique : &amp; &amp; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&&'
dev_langs:
- C++
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af091c30bddcac2a283a9040e38a62ae53c30601
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117658"
---
# <a name="logical-and-operator-ampamp"></a>Opérateur AND logique : &amp;&amp;

## <a name="syntax"></a>Syntaxe

```
expression && expression
```

## <a name="remarks"></a>Notes

L’opérateur AND logique (**&&**) retourne la valeur booléenne TRUE si les deux opérandes sont TRUE et FALSE sinon. Les opérandes sont convertis implicitement en type **bool** avant l’évaluation et le résultat est de type **bool**. L'opérateur logique présente une associativité de gauche à droite.

Les opérandes de l’opérateur logique AND n’ont pas besoin d’être du même type, mais ils doivent être de type intégral ou de type pointeur. Les opérandes sont souvent des expressions relationnelles ou d’égalité.

Le premier opérande est complètement évalué et tous les effets secondaires sont terminés avant de continuer l’évaluation de l’expression AND logique.

Le deuxième opérande est évalué uniquement si le premier opérande a la valeur true (une valeur différente de zéro). Cette évaluation élimine l’évaluation inutile du deuxième opérande lorsque l’expression AND logique est false. Vous pouvez utiliser cette évaluation de court-circuit pour empêcher le déréférencement du pointeur NULL, comme indiqué dans l'exemple suivant :

```cpp
char *pch = 0;
...
(pch) && (*pch = 'a');
```

Si `pch` est null (0), le côté droit de l'expression n'est jamais évalué. Par conséquent, l'assignation via un pointeur null est impossible.

## <a name="operator-keyword-for-"></a>Mot clé Operator pour &&

Le **et** opérateur est l’équivalent textuel de **&&**. Il existe deux façons d’accéder à la **et** opérateur dans vos programmes : inclure le fichier d’en-tête `iso646.h`, ou compiler avec la [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur (désactiver les extensions de langage).

## <a name="example"></a>Exemple

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Opérateurs C++ intégrés priorité et associativité](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs logiques C](../c-language/c-logical-operators.md)