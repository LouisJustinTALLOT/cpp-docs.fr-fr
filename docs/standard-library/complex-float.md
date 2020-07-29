---
title: complex&lt;float&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<float>
helpviewer_keywords:
- complex<float> function
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
ms.openlocfilehash: 441006c977b4a4249270d0f4809da0fba0163395
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230063"
---
# <a name="complexltfloatgt"></a>complex&lt;float&gt;

Décrit un objet qui stocke une paire ordonnée d’objets de type **`float`** , le premier représentant la partie réelle d’un nombre complexe et le deuxième représentant la partie imaginaire.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class complex<float> {
public:
    constexpr complex(
    float _RealVal = 0,
    float _ImagVal = 0);

constexpr complex(
    const complex<float>& complexNum);

constexpr complex(
    const complex<double>& complexNum);

constexpr complex(
    const complex<long double>& complexNum);
// rest same as class template complex
};
```

### <a name="parameters"></a>Paramètres

*_RealVal*\
Valeur de type **`float`** pour la partie réelle du nombre complexe en cours de construction.

*_ImagVal*\
Valeur de type **`float`** pour la partie imaginaire du nombre complexe en cours de construction.

*complexNum*\
Nombre complexe de type **`double`** ou de type **`long double`** dont les parties réelle et imaginaire sont utilisées pour initialiser un nombre complexe de type **`float`** en cours de construction.

## <a name="return-value"></a>Valeur de retour

Nombre complexe de type **`float`** .

## <a name="remarks"></a>Notes

La spécialisation explicite du modèle de classe complexe pour une classe complexe de type **`float`** diffère du modèle de classe uniquement dans les constructeurs qu’il définit. La conversion de **`float`** en **`double`** est autorisée à être implicite, mais la conversion moins sécurisée de **`float`** en doit **`long double`** obligatoirement être **`explicit`** . L’utilisation de **`explicit`** règles pour le lancement avec la conversion de type à l’aide de la syntaxe d’assignation.

Pour plus d’informations sur le modèle de classe `complex` , consultez [classe complexe](../standard-library/complex-class.md). Pour obtenir la liste des membres du modèle de classe `complex` , consultez.

## <a name="example"></a>Exemple

```cpp
// complex_comp_flt.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <float> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type double
   complex <double> c2double ( 1.0 , 3.0 );
   complex <float> c2float ( c2double );
   cout << "Implicit conversion from type double to type float,"
        << endl << "gives c2float = " << c2float << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 3.0 , 4.0 );
   complex <float> c3float ( c3longdouble );
   cout << "Explicit conversion from type long double to type float,"
        << endl << "gives c3float = " << c3float << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3float);
   double argc3 = arg ( c3float);
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:"
        << endl << "arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type double to type float,
gives c2float = (1,3)
Explicit conversion from type long double to type float,
gives c3float = (3,4)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.
*/
```

## <a name="requirements"></a>Spécifications

**En-tête**:\<complex>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Classe complexe](../standard-library/complex-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
