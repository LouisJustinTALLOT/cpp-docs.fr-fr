---
title: const_cast, opérateur
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: d2711142e4aa73cc0119949876e7e593067cd45d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180340"
---
# <a name="const_cast-operator"></a>const_cast, opérateur

Supprime le ou les attributs **const**, **volatile**et **__unaligned** d’une classe.

## <a name="syntax"></a>Syntaxe

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Notes

Un pointeur vers un type d’objet ou un pointeur vers un membre de données peut être converti explicitement en un type identique, à l’exception des qualificateurs **const**, **volatile**et **__unaligned** . Pour les pointeurs et des références, le résultat fait référence à l'objet d'origine. Pour les pointeurs vers des données membres, le résultat fait référence au même membre que le pointeur d'origine (sans cast) vers les données membres. Selon le type de l'objet référencé, une opération d'écriture via le pointeur résultant, la référence, ou le pointeur vers les données membres peut entraîner un comportement non défini.

Vous ne pouvez pas utiliser l’opérateur **const_cast** pour remplacer directement l’état constant d’une variable constante.

L’opérateur **const_cast** convertit une valeur de pointeur null en valeur de pointeur null du type de destination.

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

Sur la ligne contenant le **const_cast**, le type de données du pointeur **This** est `const CCTest *`. L’opérateur **const_cast** modifie le type de données du pointeur **This** en `CCTest *`, ce qui permet de modifier le `number` membre. Le cast dure uniquement pendant le reste de l'instruction dans laquelle il apparaît.

## <a name="see-also"></a>Voir aussi

[Opérateurs de casting](../cpp/casting-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
