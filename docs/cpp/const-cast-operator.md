---
title: const_cast, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 314e8363fafa4f2a6649055f2c608cd5b7edd18c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070077"
---
# <a name="constcast-operator"></a>const_cast, opérateur

Supprime le **const**, **volatile**, et **__unaligned** attribut (s) à partir d’une classe.

## <a name="syntax"></a>Syntaxe

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Notes

Un pointeur vers n’importe quel type d’objet ou un pointeur vers un membre de données peut être converti explicitement en un type qui est identique à l’exception de la **const**, **volatile**, et **__unaligned** qualificateurs. Pour les pointeurs et des références, le résultat fait référence à l'objet d'origine. Pour les pointeurs vers des données membres, le résultat fait référence au même membre que le pointeur d'origine (sans cast) vers les données membres. Selon le type de l'objet référencé, une opération d'écriture via le pointeur résultant, la référence, ou le pointeur vers les données membres peut entraîner un comportement non défini.

Vous ne pouvez pas utiliser le **const_cast** opérateur pour substituer directement l’état constant d’une variable constante.

Le **const_cast** opérateur convertit une valeur de pointeur null à la valeur de pointeur null du type de destination.

## <a name="example"></a>Exemple

```cpp
// expre_const_cast_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CCTest {
public:
   void setNumber( int );
   void printNumber() const;
private:
   int number;
};

void CCTest::setNumber( int num ) { number = num; }

void CCTest::printNumber() const {
   cout << "\nBefore: " << number;
   const_cast< CCTest * >( this )->number--;
   cout << "\nAfter: " << number;
}

int main() {
   CCTest X;
   X.setNumber( 8 );
   X.printNumber();
}
```

Sur la ligne contenant le **const_cast**, le type de données de la **cela** pointeur est `const CCTest *`. Le **const_cast** opérateur change le type de données de la **cela** pointeur vers `CCTest *`, ce qui permet le membre `number` à modifier. Le cast dure uniquement pendant le reste de l'instruction dans laquelle il apparaît.

## <a name="see-also"></a>Voir aussi

[Opérateurs de casting](../cpp/casting-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)