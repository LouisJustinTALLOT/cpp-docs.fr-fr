---
description: 'En savoir plus sur : classe complexe'
title: complexe, classe
ms.date: 03/27/2019
f1_keywords:
- complex/std::complex::value_type
- complex/std::complex::imag
- complex/std::complex::real
helpviewer_keywords:
- std::complex [C++], value_type
- std::complex [C++], imag
- std::complex [C++], real
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
ms.openlocfilehash: 224b59e79119496ea7484378a010c4861f32e404
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233901"
---
# <a name="complex-class"></a>complexe, classe

Le modèle de classe décrit un objet qui stocke deux objets de type `Type` , un qui représente la partie réelle d’un nombre complexe et un qui représente la partie imaginaire.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class complex
```

## <a name="remarks"></a>Notes

Objet de classe `Type` :

- A un constructeur public par défaut, un destructeur, un constructeur de copie et un opérateur d’assignation avec un comportement conventionnel.

- Peut recevoir des valeurs entières ou des valeurs à virgule flottante, ou effectuer un cast de type vers ces valeurs avec un comportement conventionnel.

- Définit les opérateurs arithmétiques et les fonctions mathématiques, selon les besoins, qui sont définis pour les types à virgule flottante avec un comportement conventionnel.

En particulier, aucune différence même minime ne peut exister entre la construction de copie et la construction par défaut suivie de l'affectation. Aucune des opérations sur les objets de la classe `Type` ne peut lever des exceptions.

Des spécialisations explicites de modèle de classe complexe existent pour les trois types à virgule flottante. Dans cette implémentation, une valeur de tout autre type est convertie `Type` en **`double`** pour les calculs réels, le **`double`** résultat étant affecté à l’objet stocké de type `Type` .

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[complexe](#complex)|Construit un nombre complexe à l'aide de la partie réelle et de la partie imaginaire spécifiées ou en tant que copie d'un autre nombre complexe.|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|[value_type](#value_type)|Type qui représente le type de données utilisé pour représenter les parties imaginaire et réelle d’un nombre complexe.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[imag](#imag)|Extrait le composant imaginaire d'un nombre complexe.|
|[real](#real)|Extrait le composant réel d'un nombre complexe.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur * =](#op_star_eq)|Multiplie un nombre complexe cible par un facteur qui peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe.|
|[opérateur + =](#op_add_eq)|Ajoute un nombre à un nombre complexe cible, où le nombre ajouté peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe auquel il est ajouté.|
|[opérateur =](#operator-_eq)|Soustrait un nombre d’un nombre complexe cible, où le nombre soustrait peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe auquel il est ajouté.|
|[opérateur/=](#op_div_eq)|Divise un nombre complexe cible par un diviseur qui peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe.|
|[opérateur =](#op_eq)|Assigne un nombre à un nombre complexe cible, où le nombre assigné peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe auquel il est assigné.|

## <a name="complex"></a><a name="complex"></a> complexe

Construit un nombre complexe à l'aide de la partie réelle et de la partie imaginaire spécifiées ou en tant que copie d'un autre nombre complexe.

```cpp
constexpr complex(
    const T& _RealVal = 0,
    const T& _ImagVal = 0);

template <class Other>
constexpr complex(
    const complex<Other>& complexNum);
```

### <a name="parameters"></a>Paramètres

*_RealVal*\
Valeur de la partie réelle utilisée pour initialiser le nombre complexe qui est construit.

*_ImagVal*\
Valeur de la partie imaginaire utilisée pour initialiser le nombre complexe qui est construit.

*complexNum*\
Nombre complexe dont la partie réelle et la partie imaginaire sont utilisées pour initialiser le nombre complexe qui est construit.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la partie réelle stockée sur *\_ RealVal* et la partie imaginaire stockée sur *\_ Imagval*. Le deuxième constructeur initialise la partie réelle stockée à `complexNum.real()` et la partie imaginaire stockée à `complexNum.imag()` .

Dans cette implémentation, si un convertisseur ne prend pas en charge les fonctions de modèle membres, le modèle :

```cpp
template <class Other>
complex(const complex<Other>& right);
```

est remplacé par :

```cpp
complex(const complex& right);
```

qui est le constructeur de copie.

### <a name="example"></a>Exemple

```cpp
// complex_complex.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,"
        << "c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of another complex number
    complex<double> c2( c1 );
    cout << "Initializing with the real and imaginary parts of c1,"
        << " c2 = " << c2 << endl;

    // Complex numbers can be initialized in polar form
    // but will be stored in Cartesian form
    complex<double> c3( polar( sqrt( (double)8 ) , pi / 4 ) );
    cout << "c3 = polar( sqrt( 8 ) , pi / 4 ) = " << c3 << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3 );
    double argc3 = arg( c3 );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

## <a name="imag"></a><a name="imag"></a> imag

Extrait le composant imaginaire d'un nombre complexe.

```cpp
T imag() const;

T imag(const T& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Nombre complexe dont la valeur imaginaire doit être extraite.

### <a name="return-value"></a>Valeur renvoyée

Partie imaginaire du nombre complexe.

### <a name="remarks"></a>Notes

Pour un nombre complexe *a + bi*, la partie ou le composant imaginaire est *im (a + bi) = b*.

### <a name="example"></a>Exemple

```cpp
// complex_imag.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;

    complex<double> c1( 4.0 , 3.0 );
    cout << "The complex number c1 = " << c1 << endl;

    double dr1 = c1.real();
    cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

    double di1 = c1.imag();
    cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="operator"></a><a name="op_star_eq"></a> opérateur * =

Multiplie un nombre complexe cible par un facteur qui peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe.

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Nombre complexe ou nombre du même type que celui du paramètre du nombre complexe cible.

### <a name="return-value"></a>Valeur renvoyée

Nombre complexe qui a été multiplié par le nombre spécifié comme paramètre.

### <a name="remarks"></a>Notes

L’opération est surchargée pour permettre l’exécution d’opérations d’arithmétique simples sans convertir les données dans un format particulier.

### <a name="example"></a>Exemple

```cpp
// complex_op_me.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main()
{
    using namespace std;
    double pi = 3.14159265359;

    // Example of the first member function
    // type complex<double> multiplied by type complex<double>
    complex<double> cl1( polar ( 3.0 , pi / 6 ) );
    complex<double> cr1( polar ( 2.0 , pi / 3 ) );
    cout << "The left-side complex number is cl1 = " << cl1 << endl;
    cout << "The right-side complex number is cr1 = " << cr1 << endl;

    complex<double> cs1 = cl1 * cr1;
    cout << "Quotient of two complex numbers is: cs1 = cl1 * cr1 = "
        << cs1 << endl;

    // This is equivalent to the following operation
    cl1 *= cr1;
    cout << "Quotient of two complex numbers is also: cl1 *= cr1 = "
        << cl1 << endl;

    double abscl1 = abs ( cl1 );
    double argcl1 = arg ( cl1 );
    cout << "The modulus of cl1 is: " << abscl1 << endl;
    cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

    // Example of the second member function
    // type complex<double> multiplied by type double
    complex<double> cl2 ( polar ( 3.0 , pi / 6 ) );
    double cr2 = 5.0;
    cout << "The left-side complex number is cl2 = " << cl2 << endl;
    cout << "The right-side complex number is cr2 = " << cr2 << endl;

    complex<double> cs2 = cl2 * cr2;
    cout << "Quotient of two complex numbers is: cs2 = cl2 * cr2 = "
        << cs2 << endl;

    // This is equivalent to the following operation
    cl2 *= cr2;
    cout << "Quotient of two complex numbers is also: cl2 *= cr2 = "
        << cl2 << endl;

    double abscl2 = abs ( cl2 );
    double argcl2 = arg ( cl2 );
    cout << "The modulus of cl2 is: " << abscl2 << endl;
    cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl;
}
```

## <a name="operator"></a><a name="op_add_eq"></a> opérateur + =

Ajoute un nombre à un nombre complexe cible, où le nombre ajouté peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe auquel il est ajouté.

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Nombre complexe ou nombre du même type que celui du paramètre du nombre complexe cible.

### <a name="return-value"></a>Valeur renvoyée

Nombre complexe auquel le nombre spécifié comme paramètre est ajouté.

### <a name="remarks"></a>Notes

L’opération est surchargée pour permettre l’exécution d’opérations d’arithmétique simples sans convertir les données dans un format particulier.

### <a name="example"></a>Exemple

```cpp
// complex_op_pe.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> added to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 + cr1;
   cout << "The sum of the two complex numbers is: cs1 = cl1 + cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 += cr1;
   cout << "The complex number cr1 added to the complex number cl1 is:"
        << "\n cl1 += cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double added to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 + cr2;
   cout << "The sum of the two complex numbers is: cs2 = cl2 + cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 += cr2;
   cout << "The complex number cr2 added to the complex number cl2 is:"
        << "\n cl2 += cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The sum of the two complex numbers is: cs1 = cl1 + cr1 = (5,3)
The complex number cr1 added to the complex number cl1 is:
cl1 += cr1 = (5,3)
The modulus of cl1 is: 5.83095
The argument of cl1 is: 0.54042 radians, which is 30.9638 degrees.

The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The sum of the two complex numbers is: cs2 = cl2 + cr2 = (3,4)
The complex number cr2 added to the complex number cl2 is:
cl2 += cr2 = (3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 0.927295 radians, which is 53.1301 degrees.
```

## <a name="operator-"></a><a name="operator-_eq"></a> opérateur =

Soustrait un nombre d’un nombre complexe cible, où le nombre soustrait peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe auquel il est ajouté.

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Paramètres

*complexNum*\
Nombre complexe à soustraire du nombre complexe cible.

*_RealPart*\
Nombre réel à soustraire du nombre complexe cible.

### <a name="return-value"></a>Valeur renvoyée

Nombre complexe duquel le nombre spécifié comme paramètre est soustrait.

### <a name="remarks"></a>Notes

L’opération est surchargée pour permettre l’exécution d’opérations d’arithmétique simples sans convertir les données dans un format particulier.

### <a name="example"></a>Exemple

```cpp
// complex_op_se.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> subtracted from type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 - cr1;
   cout << "The difference between the two complex numbers is:"
        << "\n cs1 = cl1 - cr1 = " << cs1 << endl;

   // This is equivalent to the following operation
   cl1 -= cr1;
   cout << "Complex number cr1 subtracted from complex number cl1 is:"
        << "\n cl1 -= cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double subtracted from type complex<double>
   complex<double> cl2( 2.0 , 4.0 );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 - cr2;
   cout << "The difference between the two complex numbers is:"
        << "\n cs2 = cl2 - cr2 = " << cs2 << endl;

   // This is equivalent to the following operation
   cl2  -= cr2;
   cout << "Complex number cr2 subtracted from complex number cl2 is:"
        << "\n cl2 -= cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The difference between the two complex numbers is:
cs1 = cl1 - cr1 = (1,5)
Complex number cr1 subtracted from complex number cl1 is:
cl1 -= cr1 = (1,5)
The modulus of cl1 is: 5.09902
The argument of cl1 is: 1.3734 radians, which is 78.6901 degrees.

The left-side complex number is cl2 = (2,4)
The right-side complex number is cr2 = 5
The difference between the two complex numbers is:
cs2 = cl2 - cr2 = (-3,4)
Complex number cr2 subtracted from complex number cl2 is:
cl2 -= cr2 = (-3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 2.2143 radians, which is 126.87 degrees.
```

## <a name="operator"></a><a name="op_div_eq"></a> opérateur/=

Divise un nombre complexe cible par un diviseur qui peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe.

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>Paramètres

*complexNum*\
Nombre complexe à soustraire du nombre complexe cible.

*_RealPart*\
Nombre réel à soustraire du nombre complexe cible.

### <a name="return-value"></a>Valeur renvoyée

Nombre complexe qui a été divisé par le nombre spécifié comme paramètre.

### <a name="remarks"></a>Notes

L’opération est surchargée pour permettre l’exécution d’opérations d’arithmétique simples sans convertir les données dans un format particulier.

### <a name="example"></a>Exemple

```cpp
// complex_op_de.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> divided by type complex<double>
   complex<double> cl1( polar (3.0 , pi / 6 ) );
   complex<double> cr1( polar (2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 / cr1;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 /= cr1;
   cout << "Quotient of two complex numbers is also: cl1 /= cr1 = "
        << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> divided by type double
   complex<double> cl2( polar(3.0 , pi / 6 ) );
   double cr2 =5;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 / cr2;
   cout << "The quotient of the two complex numbers is: cs2 /= cl2 cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 /= cr2;
   cout << "Quotient of two complex numbers is also: cl2 = /cr2 = "
        << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The right-side complex number is cr1 = (1,1.73205)
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)
Quotient of two complex numbers is also: cl1 /= cr1 = (1.29904,-0.75)
The modulus of cl1 is: 1.5
The argument of cl1 is: -0.523599 radians, which is -30 degrees.

The left-side complex number is cl2 = (2.59808,1.5)
The right-side complex number is cr2 = 5
The quotient of the two complex numbers is: cs2 /= cl2 cr2 = (0.519615,0.3)
Quotient of two complex numbers is also: cl2 = /cr2 = (0.519615,0.3)
The modulus of cl2 is: 0.6
The argument of cl2 is: 0.523599 radians, which is 30 degrees.
```

## <a name="operator"></a><a name="op_eq"></a> opérateur =

Assigne un nombre à un nombre complexe cible, où le nombre assigné peut être complexe ou du même type que celui des parties réelle et imaginaire du nombre complexe auquel il est assigné.

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Nombre complexe ou nombre du même type que celui du paramètre du nombre complexe cible.

### <a name="return-value"></a>Valeur renvoyée

Nombre complexe auquel le nombre spécifié comme paramètre a été assigné.

### <a name="remarks"></a>Notes

L’opération est surchargée pour permettre l’exécution d’opérations d’arithmétique simples sans convertir les données dans un format particulier.

### <a name="example"></a>Exemple

```cpp
// complex_op_as.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> assigned to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   cl1  = cr1;
   cout << "The complex number cr1 assigned to the complex number cl1 is:"
        << "\ncl1 = cr1 = " << cl1 << endl;

   // Example of the second member function
   // type double assigned to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   cl2 = cr2;
   cout << "The complex number cr2 assigned to the complex number cl2 is:"
        << "\ncl2 = cr2 = " << cl2 << endl;

   cl2 = complex<double>(3.0, 4.0);
   cout << "The complex number (3, 4) assigned to the complex number cl2 is:"
        << "\ncl2 = " << cl2 << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The complex number cr1 assigned to the complex number cl1 is:
cl1 = cr1 = (2,-1)
The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The complex number cr2 assigned to the complex number cl2 is:
cl2 = cr2 = (5,0)
The complex number (3, 4) assigned to the complex number cl2 is:
cl2 = (3,4)
```

## <a name="real"></a><a name="real"></a> non

Extrait ou définit le composant réel d'un nombre complexe.

```cpp
constexpr T real() const;

T real(const T& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Nombre complexe dont la valeur réelle doit être extraite.

### <a name="return-value"></a>Valeur renvoyée

Partie réelle du nombre complexe.

### <a name="remarks"></a>Notes

Pour un nombre complexe *a + bi*, la partie ou le composant réel est *re (a + bi) = a*.

### <a name="example"></a>Exemple

```cpp
// complex_class_real.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex<double> c1( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real();
   cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

   double di1 = c1.imag();
   cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="value_type"></a><a name="value_type"></a> value_type

Type qui représente le type de données utilisé pour représenter les parties imaginaire et réelle d’un nombre complexe.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Notes

`value_type` est un synonyme du paramètre de modèle complexe de classe `Type` .

### <a name="example"></a>Exemple

```cpp
// complex_valuetype.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    complex<double>::value_type a = 3, b = 4;

    complex<double> c1 ( a , b );
    cout << "Specifying initial real & imaginary parts"
        << "\nof type value_type: "
        << "c1 = " << c1 << "." << endl;
}
```

```Output
Specifying initial real & imaginary parts
of type value_type: c1 = (3,4).
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
