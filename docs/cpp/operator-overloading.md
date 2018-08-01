---
title: Surcharge d’opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- operator_cpp
- operator
dev_langs:
- C++
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eae4b7cc2211462b097efbefca580b796d573c59
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408944"
---
# <a name="operator-overloading"></a>Surcharge d’opérateur

Le **opérateur** mot clé déclare une fonction spécifiant la signification *symbole d’opérateur* signifie que lorsqu’il est appliqué aux instances d’une classe. Cela donne à l'opérateur plusieurs significations ou le « surcharge ». Le compilateur fait la distinction entre les différentes significations d’un opérateur en examinant les types de ses opérandes.

## <a name="syntax"></a>Syntaxe

> *type* **opérateur** *symbole d’opérateur* **(** *liste de paramètres* **)**

## <a name="remarks"></a>Notes

Vous pouvez redéfinir la fonction de la plupart des opérateurs intégrés de manière globale ou classe par classe. Les opérateurs surchargés sont implémentés en tant que fonctions.

Le nom d’un opérateur surchargé est **opérateur** *x*, où *x* est l’opérateur tel qu’il apparaît dans le tableau suivant. Par exemple, pour surcharger l’opérateur d’addition, vous définissez une fonction appelée **opérateur +**. De même, pour surcharger l’opérateur d’addition/assignation, **+=**, définir une fonction appelée **operator +=**.

### <a name="redefinable-operators"></a>Opérateurs redéfinissables

|Opérateur|Nom|Type|
|--------------|----------|----------|
|**,**|Virgule|Binaire|
|**!**|NOT logique|Unaire|
|**\!=**|Inégalité|Binaire|
|**%**|Modulo|Binaire|
|**%=**|Assignation de modulo|Binaire|
|**&**|Opération de bits AND|Binaire|
|**&**|Adresse-de|Unaire|
|**&&**|AND logique|Binaire|
|**&=**|Assignation d'opération AND au niveau du bit|Binaire|
|**( )**|Appel de fonction |—|
|**( )**|Opérateur de cast|Unaire|
|**&#42;**|Multiplication|Binaire|
|**&#42;**|Déréférencement du pointeur|Unaire|
|**&#42;=**|Assignation de multiplication|Binaire|
|**+**|Addition|Binaire|
|**+**|Plus unaire|Unaire|
|**++**|Incrément <sup>1</sup>|Unaire|
|**+=**|Assignation d'addition|Binaire|
|**-**|Soustraction|Binaire|
|**-**|Négation unaire|Unaire|
|**--**|Décrément <sup>1</sup>|Unaire|
|**-=**|Assignation de soustraction|Binaire|
|**->**|Sélection de membres|Binaire|
|**->&#42;**|Sélection de pointeur de membre|Binaire|
|**/**|Division|Binaire|
|**/=**|Assignation de division|Binaire|
|**\<**|Inférieur à|Binaire|
|**<<**|Décalage vers la gauche|Binaire|
|**<<=**|Assignation de décalage vers la gauche|Binaire|
|**<=**|Inférieur ou égal à|Binaire|
|**=**|Assignation|Binaire|
|**==**|Égalité|Binaire|
|**>**|Supérieur à|Binaire|
|**>=**|Supérieur ou égal à|Binaire|
|**>>**|Décalage vers la droite|Binaire|
|**>>=**|Assignation de décalage vers la droite|Binaire|
|**[ ]**|Indice de tableau|—|
|**^**|OR exclusive|Binaire|
|**^=**|Assignation OR exclusive|Binaire|
|**&#124;**|Opération de bits OR inclusive|Binaire|
|**&#124;=**|Assignation d'opération OR inclusive au niveau du bit|Binaire|
|**&#124;&#124;**|OR logique|Binaire|
|**~**|Complément à 1|Unaire|
|**delete**|Supprimer|—|
|**new**|Nouveau|—|
|opérateurs de conversion|opérateurs de conversion|Unaire|

<sup>1</sup> deux versions de l’unaire incrémentent et opérateurs de décrément existent : préincrément et postincrément.

Consultez [règles générales pour la surcharge d’opérateur](../cpp/general-rules-for-operator-overloading.md) pour plus d’informations. Les contraintes sur les différentes catégories d'opérateurs surchargés sont décrites dans les rubriques suivantes :

- [Opérateurs unaires](../cpp/overloading-unary-operators.md)

- [Opérateurs binaires](../cpp/binary-operators.md)

- [Attribution](../cpp/assignment.md)

- [Appel de fonction ](../cpp/function-call-cpp.md)

- [Indices](../cpp/subscripting.md)

- [Accès aux membres de classe](../cpp/member-access.md)

- [Incrémentation et décrémentation](../cpp/increment-and-decrement-operator-overloading-cpp.md).

- [Conversions de type définies par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md)

Les opérateurs indiqués dans le tableau suivant ne peuvent pas être surchargés. Le tableau inclut les symboles de préprocesseur **#** et **##**.

### <a name="nonredefinable-operators"></a>Opérateurs non redéfinissables

|Opérateur|Name|
|-|-|
|**.**|Sélection de membres|
|**.&#42;**|Sélection de pointeur de membre|
|**::**|Résolution de portée|
|**? :**|Conditionnel|
|**#**|Préprocesseur convertir en type string|
|**##**|Préprocesseur concaténer|

Bien que les opérateurs surchargés soient généralement appelés implicitement par le compilateur quand ils sont trouvés dans le code, ils peuvent être invoqués explicitement de la même façon que n'importe quelle fonction membre ou non membre :

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>Exemple

L’exemple suivant surcharge la **+** opérateur pour ajouter deux nombres complexes et retourne le résultat.

```cpp
// operator_overloading.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Complex {
   Complex( double r, double i ) : re(r), im(i) {}
   Complex operator+( Complex &other );
   void Display( ) {   cout << re << ", " << im << endl; }
private:
   double re, im;
};

// Operator overloaded using a member function
Complex Complex::operator+( Complex &other ) {
   return Complex( re + other.re, im + other.im );
}

int main() {
   Complex a = Complex( 1.2, 3.4 );
   Complex b = Complex( 5.6, 7.8 );
   Complex c = Complex( 0.0, 0.0 );

   c = a + b;
   c.Display();
}
```

```Output
6.8, 11.2
```

## <a name="in-this-section"></a>Dans cette section

- [Règles générales de surcharge d’opérateur](../cpp/general-rules-for-operator-overloading.md)

- [Surcharge des opérateurs unaires](../cpp/overloading-unary-operators.md)

- [Opérateurs binaires](../cpp/binary-operators.md)

- [Attribution](../cpp/assignment.md)

- [Appel de fonction ](../cpp/function-call-cpp.md)

- [Indices](../cpp/subscripting.md)

- [Accès au membre](../cpp/member-access.md)

## <a name="see-also"></a>Voir aussi
 [Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 [Mots clés](../cpp/keywords-cpp.md)