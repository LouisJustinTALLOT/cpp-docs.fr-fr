---
title: '&lt;ios&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::defaultfloat
- xiosbase/std::boolalpha
- xiosbase/std::dec
- ios/std::fixed
- ios/std::hex
- ios/std::internal
- ios/std::left
- ios/std::noboolalpha
- ios/std::noshowbase
- ios/std::noshowpoint
- ios/std::noshowpos
- ios/std::noskipws
- ios/std::nounitbuf
- ios/std::nouppercase
- ios/std::oct
- ios/std::right
- ios/std::scientific
- ios/std::showbase
- ios/std::showpoint
- ios/std::showpos
- ios/std::skipws
- ios/std::unitbuf
- ios/std::uppercase
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::hexfloat [C++]
- std::io_errc [C++]
- std::internal [C++]
- std::iostream_category [C++]
- std::is_error_code_enum [C++]
- std::left [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::noboolalpha [C++]
- std::noshowbase [C++]
- std::noshowpoint [C++]
- std::noshowpos [C++]
- std::noskipws [C++]
- std::nounitbuf [C++]
- std::nouppercase [C++]
- std::oct [C++]
- std::right [C++]
- std::scientific [C++]
- std::showbase [C++]
- std::showpoint [C++]
- std::showpos [C++]
- std::skipws [C++]
- std::unitbuf [C++]
- std::uppercase [C++]
ms.openlocfilehash: a750f17ba8eba40dd01a2fb4a89e47a0927e4b61
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212291"
---
# <a name="ltiosgt-functions"></a>&lt;ios&gt;, fonctions

## <a name="boolalpha"></a><a name="boolalpha"></a>boolalpha

Spécifie que les variables de type [bool](../cpp/bool-cpp.md) apparaissent comme **`true`** ou **`false`** dans le flux.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, les variables de type **`bool`** sont affichées comme 1 ou 0.

`boolalpha`appelle `str.` [SETF](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha` ), puis retourne *Str*.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) inverse l’effet de `boolalpha`.

### <a name="example"></a>Exemple

```cpp
// ios_boolalpha.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   bool b = true;
   cout << b << endl;
   boolalpha( cout );
   cout << b << endl;
   noboolalpha( cout );
   cout << b << endl;
   cout << boolalpha << b << endl;
}
```

```Output
1
true
1
true
```

## <a name="dec"></a><a name="dec"></a>decembre

Indique que les variables de type entier sont affichées en notation de base 10.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, les variables de type entier sont affichées en base 10.

`dec`appelle `str.` [SETF](../standard-library/ios-base-class.md#setf)( `ios_base::dec` , `ios_base::basefield` ), puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_dec.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 100;

   cout << i << endl;   // Default is base 10
   cout << hex << i << endl;
   dec( cout );
   cout << i << endl;
   oct( cout );
   cout << i << endl;
   cout << dec << i << endl;
}
```

```Output
100
64
100
144
100
```

## <a name="ltiosgt-defaultfloat"></a><a name="ios_defaultfloat"></a> &lt;ios&gt; defaultfloat

Configure les indicateurs d'un objet `ios_base` pour utiliser un format d'affichage par défaut pour les valeurs de type float.

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>Paramètres

*_Iosbase*\
Objet `ios_base`.

### <a name="remarks"></a>Notes

Le manipulateur appelle effectivement `iosbase.` [ios_base :: unsetf](../standard-library/ios-base-class.md#unsetf) `(ios_base::floatfield)` , puis retourne *iosbase*.

## <a name="fixed"></a><a name="fixed"></a>des

Indique qu'un nombre à virgule flottante est affiché en notation décimale fixe.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

`fixed`est la notation d’affichage par défaut pour les nombres à virgule flottante. [scientific](../standard-library/ios-functions.md#scientific) fait en sorte que les nombres à virgule flottante soient affichés à l’aide de la notation scientifique.

Le manipulateur appelle effectivement *Str*. [SETF](../standard-library/ios-base-class.md#setf)( `ios_base::fixed` , `ios_base::floatfield` ), puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_fixed.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 1.1F;

   cout << i << endl;   // fixed is the default
   cout << scientific << i << endl;
   cout.precision( 1 );
   cout << fixed << i << endl;
}
```

```Output
1.1
1.100000e+000
1.1
```

## <a name="hex"></a><a name="hex"></a>séquence

Indique que les variables de type entier sont affichées en notation de base 16.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, les variables de type entier sont affichées en notation de base 10. [dec](../standard-library/ios-functions.md#dec) et [oct](../standard-library/ios-functions.md#oct) modifient également le mode d’affichage des variables de type entier.

Le manipulateur appelle effectivement `str` **.** [SETF](../standard-library/ios-base-class.md#setf)( `ios_base::hex` , `ios_base::basefield` ), puis retourne *Str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, reportez-vous à [Dec](../standard-library/ios-functions.md#dec) `hex` .

## <a name="hexfloat"></a><a name="hexfloat"></a>hexfloat

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a><a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a><a name="internal"></a>intérieurs

Aligne à gauche le signe d'un nombre et aligne à droite le nombre.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

[showpos](../standard-library/ios-functions.md#showpos) provoque l’affichage du signe pour les nombres positifs.

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(` [ios_base :: Internal](../standard-library/ios-base-class.md#fmtflags) `,` [ios_base :: adjustfield](../standard-library/ios-base-class.md#fmtflags) `)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_internal.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( void )
{
   using namespace std;
   float i = -123.456F;
   cout.fill( '.' );
   cout << setw( 10 ) << i << endl;
   cout << setw( 10 ) << internal << i << endl;
}
```

```Output
..-123.456
-..123.456
```

## <a name="is_error_code_enum"></a><a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a><a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a><a name="left"></a>gauche

Fait en sorte que le texte qui n'est pas aussi large que la largeur de sortie apparaisse dans le flux aligné avec la marge de gauche.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(ios_base::left, ios_base::adjustfield)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_left.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout.width( 20 );
   cout << f1 << endl;
   cout << left << f1 << endl;
}
```

```Output
5
        5
```

## <a name="make_error_code"></a><a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a><a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a><a name="noboolalpha"></a>noboolalpha

Indique que les variables de type [bool](../cpp/bool-cpp.md) apparaissent comme 1 ou 0 dans le flux.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, `noboolalpha` est activé.

`noboolalpha`appelle `str.` [unsetf](../standard-library/ios-base-class.md#unsetf) `(ios_base::boolalpha)` , puis retourne *Str*.

[boolalpha](../standard-library/ios-functions.md#boolalpha) inverse l’effet de `noboolalpha`.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `noboolalpha`, consultez [boolalpha](../standard-library/ios-functions.md#boolalpha).

## <a name="noshowbase"></a><a name="noshowbase"></a>noshowbase

Désactive l'indication de la base de notation dans laquelle un nombre est affiché.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

`noshowbase` est activé par défaut. Utilisez [showbase](../standard-library/ios-functions.md#showbase) pour indiquer la base notationnelle des nombres.

Le manipulateur appelle `str.` [unsetf](../standard-library/ios-base-class.md#unsetf) `(ios_base::showbase)` , puis retourne *Str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `noshowbase`, consultez [showbase](../standard-library/ios-functions.md#showbase).

## <a name="noshowpoint"></a><a name="noshowpoint"></a>noshowpoint

Affiche uniquement la partie entière des nombres à virgule flottante dont la partie fractionnaire est égale à zéro.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

`noshowpoint` est activé par défaut. Utilisez [showpoint](../standard-library/ios-functions.md#showpoint) et [precision](../standard-library/ios-base-class.md#precision) pour afficher les zéros non significatifs après la virgule décimale.

Le manipulateur appelle `str.` [unsetf](../standard-library/ios-base-class.md#unsetf) `(ios_base::showpoint)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_noshowpoint.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.000;
   cout << f1 << endl;   // noshowpoint is default
   cout.precision( 4 );
   cout << showpoint << f1 << endl;
   cout << noshowpoint << f1 << endl;
}
```

```Output
5
5.000
5
```

## <a name="noshowpos"></a><a name="noshowpos"></a>noshowpos

Fait en sorte que les nombres positifs ne soient pas signés explicitement.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

`noshowpos` est activé par défaut.

Le manipulateur appelle `str.` [unsetf](../standard-library/ios-base-class.md#unsetf) `(ios_base::showps)` , puis retourne *Str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `noshowpos`, consultez [showpos](../standard-library/ios-functions.md#showpos).

## <a name="noskipws"></a><a name="noskipws"></a>noskipws

Fait en sorte que les espaces soient lus par le flux d'entrée.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, [skipws](../standard-library/ios-functions.md#skipws) est activé. La lecture d’un espace dans le flux d’entrée signale la fin de la mémoire tampon.

Le manipulateur appelle `str.` [unsetf](../standard-library/ios-base-class.md#unsetf) `(ios_base::skipws)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_noskipws.cpp
// compile with: /EHsc
#include <iostream>
#include <string>

int main() {
   using namespace std;
   string s1, s2, s3;
   cout << "Enter three strings: ";
   cin >> noskipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

## <a name="nounitbuf"></a><a name="nounitbuf"></a>nounitbuf

Fait en sorte que la sortie soit mise en mémoire tampon et traitée quand la mémoire tampon est pleine.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

[unitbuf](../standard-library/ios-functions.md#unitbuf) fait en sorte que la mémoire tampon soit traitée quand elle n’est pas vide.

Le manipulateur appelle `str.` [unsetf](../standard-library/ios-base-class.md#unsetf) `(ios_base::unitbuf)` , puis retourne *Str*.

## <a name="nouppercase"></a><a name="nouppercase"></a>nouppercase

Spécifie que les chiffres hexadécimaux et l'exposant en notation scientifique apparaissent en minuscules.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Le manipulateur appelle `str.` [unsetf](../standard-library/ios-base-class.md#unsetf) `(ios_base::uppercase)` , puis retourne *Str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `nouppercase`, consultez [uppercase](../standard-library/ios-functions.md#uppercase).

## <a name="oct"></a><a name="oct"></a>personnalisation

Indique que les variables de type entier sont affichées en notation de base 8.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, les variables de type entier sont affichées en notation de base 10. [dec](../standard-library/ios-functions.md#dec) et [hex](../standard-library/ios-functions.md#hex) modifient également le mode d’affichage des variables de type entier.

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(ios_base::oct, ios_base::basefield)` , puis retourne *Str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, reportez-vous à [Dec](../standard-library/ios-functions.md#dec) `oct` .

## <a name="right"></a><a name="right"></a>Oui

Fait en sorte que le texte qui n'est pas aussi large que la largeur de sortie apparaisse dans le flux aligné avec la marge de droite.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

[left](../standard-library/ios-functions.md#left) modifie également la justification du texte.

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(ios_base::right, ios_base::adjustfield)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_right.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << left << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << right << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
}
```

```Output
5
                   5
5
5
                   5
                   5
```

## <a name="scientific"></a><a name="scientific"></a>nature

Fait en sorte que les nombres à virgule flottante soient affichés à l’aide de la notation scientifique.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, la notation [fixed](../standard-library/ios-functions.md#fixed) est appliquée pour les nombres à virgule flottante.

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(ios_base::scientific, ios_base::floatfield)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_scientific.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 100.23F;

   cout << i << endl;
   cout << scientific << i << endl;
}
```

```Output
100.23
1.002300e+002
```

## <a name="showbase"></a><a name="showbase"></a>ShowBase

Indique la base de notation dans laquelle un nombre est affiché.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

La base notationnelle d’un nombre significatif peut être modifiée avec [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct) ou [hex](../standard-library/ios-functions.md#hex).

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(ios_base::showbase)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_showbase.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int j = 100;

   cout << showbase << j << endl;   // dec is default
   cout << hex << j << showbase << endl;
   cout << oct << j << showbase << endl;

   cout << dec << j << noshowbase << endl;
   cout << hex << j << noshowbase << endl;
   cout << oct << j << noshowbase << endl;
}
```

```Output
100
0x64
0144
100
64
144
```

## <a name="showpoint"></a><a name="showpoint"></a>showpoint

Affiche la partie entière d'un nombre à virgule flottante et les chiffres à droite de la virgule décimale même quand la partie fractionnaire est égale à zéro.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, [noshowpoint](../standard-library/ios-functions.md#noshowpoint) est activé.

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(ios_base::showpoint)` , puis retourne *Str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `showpoint`, consultez [noshowpoint](../standard-library/ios-functions.md#noshowpoint).

## <a name="showpos"></a><a name="showpos"></a>showpos

Fait en sorte que les nombres positifs soient signés explicitement.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

[noshowpos](../standard-library/ios-functions.md#noshowpos) est la valeur par défaut.

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(ios_base::showpos)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_showpos.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 1;

   cout << noshowpos << i << endl;   // noshowpos is default
   cout << showpos << i << endl;
}
```

```Output
1
+1
```

## <a name="skipws"></a><a name="skipws"></a>skipws

Fait en sorte que les espaces ne soient pas lus par le flux d'entrée.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, `skipws` est activé. [noskipws](../standard-library/ios-functions.md#noskipws) fait en sorte que les espaces soient lus à partir du flux d’entrée.

Le manipulateur appelle `str.` [SETF](../standard-library/ios-base-class.md#setf) `(ios_base::skipws)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   char s1, s2, s3;
   cout << "Enter three characters: ";
   cin >> skipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

```Input
1 2 3
```

```Output
Enter three characters: 1 2 3
.1.
.2.
.3.
```

## <a name="unitbuf"></a><a name="unitbuf"></a>unitbuf

Fait en sorte que la sortie soit traitée quand la mémoire tampon n'est pas vide.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Notez que `endl` vide aussi la mémoire tampon.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) est activé par défaut.

Le manipulateur appelle le `str.` [SETF](../standard-library/ios-base-class.md#setf) `(` [ios_base :: unitbuf](../standard-library/ios-base-class.md#fmtflags) `)` , puis retourne *Str*.

## <a name="uppercase"></a><a name="uppercase"></a>capitale

Spécifie que les chiffres hexadécimaux et l'exposant en notation scientifique apparaissent en majuscules.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, [nouppercase](../standard-library/ios-functions.md#nouppercase) est activé.

Le manipulateur appelle le `str.` [SETF](../standard-library/ios-base-class.md#setf) `(` [ios_base :: uppercase](../standard-library/ios-base-class.md#fmtflags) `)` , puis retourne *Str*.

### <a name="example"></a>Exemple

```cpp
// ios_uppercase.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
   using namespace std;

   double i = 1.23e100;
   cout << i << endl;
   cout << uppercase << i << endl;

   int j = 10;
   cout << hex << nouppercase << j << endl;
   cout << hex << uppercase << j << endl;
}
```

```Output
1.23e+100
1.23E+100
a
A
```
