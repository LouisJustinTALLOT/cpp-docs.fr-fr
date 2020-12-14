---
description: 'En savoir plus sur : complexe &lt; long double&gt;'
title: complex&lt;long double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 5dd3b50c28b889a2e1fafba37cc24fda832f5975
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233823"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

Ce modèle de classe explicitement spécialisé décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **`long double`** , le premier représentant la partie réelle d’un nombre complexe et le deuxième représentant la partie imaginaire.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);

// rest same as class template complex
};
```

### <a name="parameters"></a>Paramètres

*_RealVal*\
Valeur de type **`long double`** pour la partie réelle du nombre complexe en cours de construction.

*_ImagVal*\
Valeur de type **`long double`** pour la partie imaginaire du nombre complexe en cours de construction.

*complexNum*\
Nombre complexe de type **`double`** ou de type **`float`** dont les parties réelle et imaginaire sont utilisées pour initialiser un nombre complexe de type **`long double`** en cours de construction.

## <a name="return-value"></a>Valeur renvoyée

Nombre complexe de type **`long double`** .

## <a name="remarks"></a>Notes

La spécialisation explicite du modèle de classe `complex` à une classe complexe de type **`long double`** diffère du modèle de classe uniquement dans les constructeurs qu’il définit. La conversion de **`long double`** en **`float`** est autorisée à être implicite, mais la conversion de **`double`** en doit **`long double`** obligatoirement être **`explicit`** . L’utilisation de **`explicit`** règles pour le lancement avec la conversion de type à l’aide de la syntaxe d’assignation.

Pour plus d’informations sur le modèle de classe `complex` et ses membres, consultez [classe complexe](../standard-library/complex-class.md).

**Spécifique à Microsoft**: les **`long double`** **`double`** types et ont la même représentation, mais sont des types distincts. Pour plus d’informations, consultez [types intégrés](../cpp/fundamental-types-cpp.md).

## <a name="example"></a>Exemple

```cpp
// complex_comp_ld.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<long double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of complex number of type float
    complex<float> c2float( 1.0 , 3.0 );
    complex<long double> c2longdouble ( c2float );
    cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

    // The third constructor initializes values of the real &
    // imaginary parts using those of a complex number
    // of type double
    complex<double> c3double( 3.0 , 4.0 );
    complex<long double> c3longdouble( c3double );
    cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3longdouble );
    double argc3 = arg( c3longdouble );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

```Output
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg( c3 ) = 0.927295 radians, which is 53.1301 degrees.
```

## <a name="requirements"></a>Spécifications

**En-tête**: \<complex>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe complexe](../standard-library/complex-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
