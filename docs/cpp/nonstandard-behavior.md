---
description: 'En savoir plus sur : comportement non standard'
title: Comportement non standard
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: 9f696582b23dfd4a22e6d48b9294a79787518b50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330847"
---
# <a name="nonstandard-behavior"></a>Comportement non standard

Les sections suivantes répertorient certains des endroits où l’implémentation Microsoft de C++ n’est pas conforme à la norme C++. Les numéros de section ci-dessous correspondent aux numéros de section de la norme C++11 (ISO/IEC 14882:2011(E)).

La liste des limites du compilateur qui diffèrent de celles définies dans la norme C++ est indiquée dans les [limites du compilateur](../cpp/compiler-limits.md).

## <a name="covariant-return-types"></a>Types de retour covariant

Les classes de base virtuelle ne sont pas prises en charge en tant que types de retour covariants lorsque la fonction virtuelle a un nombre d’arguments variable. Ceci n'est pas conforme à la section 10.3, paragraphe 7 de la spécification ISO C++. L’exemple suivant ne compile pas, ce qui donne une erreur du compilateur [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)

```cpp
// CovariantReturn.cpp
class A
{
   virtual A* f(int c, ...);   // remove ...
};

class B : virtual A
{
   B* f(int c, ...);   // C2688 remove ...
};
```

## <a name="binding-nondependent-names-in-templates"></a>Liaison de noms non dépendants dans des modèles

Le compilateur Microsoft C++ ne prend actuellement pas en charge la liaison de noms non dépendants lors de l’analyse initiale d’un modèle. Ceci n'est pas conforme à la section 14.6.3 de la spécification ISO C++. Cela peut provoquer la déclaration de surcharges après le modèle à afficher (mais avant que le modèle soit instancié).

```cpp
#include <iostream>
using namespace std;

namespace N {
   void f(int) { cout << "f(int)" << endl;}
}

template <class T> void g(T) {
    N::f('a');   // calls f(char), should call f(int)
}

namespace N {
    void f(char) { cout << "f(char)" << endl;}
}

int main() {
    g('c');
}
// Output: f(char)
```

## <a name="function-exception-specifiers"></a>Spécificateurs d'exceptions de fonctions

Les spécificateurs d'exceptions de fonction autres que `throw()` sont analysés, mais pas utilisés. Ceci n'est pas conforme à la section 15.4 de la spécification ISO C++. Par exemple :

```cpp
void f() throw(int); // parsed but not used
void g() throw();    // parsed and used
```

Pour plus d’informations sur les spécifications d’exceptions, consultez [spécifications d’exception](../cpp/exception-specifications-throw-cpp.md).

## <a name="char_traitseof"></a>char_traits::eof()

La norme C++ indique que [char_traits :: EOF](../standard-library/char-traits-struct.md#eof) ne doit pas correspondre à une `char_type` valeur valide. Le compilateur Microsoft C++ applique cette contrainte pour le type **`char`** , mais pas pour le type **`wchar_t`** . Ceci n’est pas conforme à l’exigence du tableau 62 de la section 12.1.1 de la spécification ISO C++. C'est ce qu'illustre l'exemple ci-dessous.

```cpp
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

## <a name="storage-location-of-objects"></a>Emplacement de stockage des objets

La norme C++ (section 1.8, paragraphe 6) exige que les objets C++ complets aient des emplacements de stockage uniques. Toutefois, avec Microsoft C++, il existe des cas où les types sans données membres partagent un emplacement de stockage avec d’autres types pendant la durée de vie de l’objet.
