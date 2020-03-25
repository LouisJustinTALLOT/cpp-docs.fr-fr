---
title: Surcharge d'opérateur
ms.date: 11/04/2016
f1_keywords:
- operator_cpp
- operator
helpviewer_keywords:
- redefinable operators [C++]
- non-redefinable operators [C++]
- operator keyword [C++]
- operators [C++], overloading
- operator overloading
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
ms.openlocfilehash: a16f68088ffffd6c3cf38f5ae3adda5f2d59fb57
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188569"
---
# <a name="operator-overloading"></a>Surcharge d’opérateur

Le mot clé **Operator** déclare une fonction qui spécifie ce que signifie *Operator-Symbol* lorsqu’il est appliqué aux instances d’une classe. Cela donne à l'opérateur plusieurs significations ou le « surcharge ». Le compilateur fait la distinction entre les différentes significations d’un opérateur en examinant les types de ses opérandes.

## <a name="syntax"></a>Syntaxe

> *type* **Operator** *opérateur-Symbol* **(** *parameter-list* **)**

## <a name="remarks"></a>Notes

Vous pouvez redéfinir la fonction de la plupart des opérateurs intégrés de manière globale ou classe par classe. Les opérateurs surchargés sont implémentés en tant que fonctions.

Le nom d’un opérateur surchargé est l' **opérateur** *x*, où *x* est l’opérateur tel qu’il apparaît dans le tableau suivant. Par exemple, pour surcharger l’opérateur d’addition, vous définissez une fonction appelée **Operator +** . De même, pour surcharger l’opérateur d’addition/assignation, **+=** , définissez une fonction appelée **opérateur + =** .

### <a name="redefinable-operators"></a>Opérateurs redéfinissables

|Opérateur|Name|Type|
|--------------|----------|----------|
|**,**|Comma|Binary|
|**!**|NOT logique|Unaire|
|**!=**|Inégalité|Binary|
|**%**|Modulus|Binary|
|**%=**|Assignation de modulo|Binary|
|**&**|ET au niveau du bit|Binary|
|**&**|Adresse-de|Unaire|
|**&&**|ET logique|Binary|
|**&=**|Assignation d'opération AND au niveau du bit|Binary|
|**( )**|Appel de fonction|—|
|**( )**|Opérateur de conversion|Unaire|
|**&#42;**|Multiplication|Binary|
|**&#42;**|Déréférencement du pointeur|Unaire|
|**&#42;=**|Assignation de multiplication|Binary|
|**+**|Addition|Binary|
|**+**|Plus unaire|Unaire|
|**++**|Incrément <sup>1</sup>|Unaire|
|**+=**|Assignation d'addition|Binary|
|**-**|Soustraction|Binary|
|**-**|Négation unaire|Unaire|
|**--**|Décrémentation <sup>1</sup>|Unaire|
|**-=**|Assignation de soustraction|Binary|
|**->**|Sélection de membres|Binary|
|**->&#42;**|Sélection de pointeur de membre|Binary|
|**/**|Division|Binary|
|**/=**|Assignation de division|Binary|
|**\<**|Inférieur à|Binary|
|**<<**|Décalage vers la gauche|Binary|
|**<<=**|Assignation de décalage vers la gauche|Binary|
|**<=**|Inférieur ou égal à|Binary|
|**=**|Affectation|Binary|
|**==**|Égalité|Binary|
|**>**|Supérieur à|Binary|
|**>=**|Supérieur ou égal à|Binary|
|**>>**|Décalage vers la droite|Binary|
|**>>=**|Assignation de décalage vers la droite|Binary|
|**[ ]**|Indice de tableau|—|
|**^**|OR exclusive|Binary|
|**^=**|Assignation OR exclusive|Binary|
|**&#124;**|Opération OR inclusive au niveau du bit|Binary|
|**&#124;=**|Assignation d'opération OR inclusive au niveau du bit|Binary|
|**&#124;&#124;**|OU logique|Binary|
|**~**|Complément à 1|Unaire|
|**delete**|DELETE|—|
|**nouveau**|Nouveau|—|
|opérateurs de conversion|opérateurs de conversion|Unaire|

<sup>1</sup> deux versions des opérateurs d’incrémentation et de décrémentation unaires existent : precrement et postincrémentation.

Pour plus d’informations, consultez [règles générales pour la surcharge d’opérateur](../cpp/general-rules-for-operator-overloading.md) . Les contraintes sur les différentes catégories d'opérateurs surchargés sont décrites dans les rubriques suivantes :

- [Opérateurs unaires](../cpp/overloading-unary-operators.md)

- [Opérateurs binaires](../cpp/binary-operators.md)

- [Affectation](../cpp/assignment.md)

- [Appel de fonction ](../cpp/function-call-cpp.md)

- [Indices](../cpp/subscripting.md)

- [Accès au membre de classe](../cpp/member-access.md)

- [Incrémentation et décrémentation](../cpp/increment-and-decrement-operator-overloading-cpp.md).

- [Conversions de type définies par l’utilisateur](../cpp/user-defined-type-conversions-cpp.md)

Les opérateurs indiqués dans le tableau suivant ne peuvent pas être surchargés. La table comprend les symboles de préprocesseur **#** et **##** .

### <a name="nonredefinable-operators"></a>Opérateurs non redéfinissables

|Opérateur|Name|
|-|-|
|**.**|Sélection de membres|
|**.&#42;**|Sélection de pointeur de membre|
|**::**|Résolution de portée|
|**? :**|Logique conditionnelle|
|**#**|Préprocesseur convertir en type string|
|**##**|Préprocesseur concaténer|

Bien que les opérateurs surchargés soient généralement appelés implicitement par le compilateur quand ils sont trouvés dans le code, ils peuvent être invoqués explicitement de la même façon que n'importe quelle fonction membre ou non membre :

```cpp
Point pt;
pt.operator+( 3 );  // Call addition operator to add 3 to pt.
```

## <a name="example"></a>Exemple

L’exemple suivant surcharge l’opérateur **+** pour ajouter deux nombres complexes et retourne le résultat.

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

## <a name="in-this-section"></a>Contenu de cette section

- [Règles générales de surcharge d’opérateur](../cpp/general-rules-for-operator-overloading.md)

- [Surcharge des opérateurs unaires](../cpp/overloading-unary-operators.md)

- [Opérateurs binaires](../cpp/binary-operators.md)

- [Affectation](../cpp/assignment.md)

- [Appel de fonction ](../cpp/function-call-cpp.md)

- [Indices](../cpp/subscripting.md)

- [Accès au membre](../cpp/member-access.md)

## <a name="see-also"></a>Voir aussi

[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
