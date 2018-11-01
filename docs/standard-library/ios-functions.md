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
- std::internal [C++]
- std::left [C++]
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
ms.openlocfilehash: bf22c0e4775ef93b1965a7c9d61f024441bea821
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509680"
---
# <a name="ltiosgt-functions"></a>&lt;ios&gt;, fonctions

||||
|-|-|-|
|[defaultfloat](#ios_defaultfloat)|[boolalpha](#boolalpha)|[dec](#dec)|
|[fixed](#fixed)|[hex](#hex)|[internal](#internal)|
|[left](#left)|[noboolalpha](#noboolalpha)|[noshowbase](#noshowbase)|
|[noshowpoint](#noshowpoint)|[noshowpos](#noshowpos)|[noskipws](#noskipws)|
|[nounitbuf](#nounitbuf)|[nouppercase](#nouppercase)|[oct](#oct)|
|[right](#right)|[scientific](#scientific)|[showbase](#showbase)|
|[showpoint](#showpoint)|[showpos](#showpos)|[skipws](#skipws)|
|[unitbuf](#unitbuf)|[uppercase](#uppercase)|

## <a name="boolalpha"></a>  boolalpha

Indique que les variables de type [bool](../cpp/bool-cpp.md) apparaissent comme **true** ou **false** dans le flux.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, les variables de type **bool** sont affichés sous forme de 1 ou 0.

`boolalpha` appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha`), puis retourne *str*.

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

## <a name="dec"></a>  dec

Indique que les variables de type entier sont affichées en notation de base 10.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, les variables de type entier sont affichées en base 10.

`dec` appelle `str.` [setf](../standard-library/ios-base-class.md#setf)( `ios_base::dec`, `ios_base::basefield`), puis retourne *str*.

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

## <a name="ios_defaultfloat"></a>  &lt;ios&gt; defaultfloat

Configure les indicateurs d'un objet `ios_base` pour utiliser un format d'affichage par défaut pour les valeurs de type float.

```cpp
ios_base& defaultfloat(ios_base& _Iosbase);
```

### <a name="parameters"></a>Paramètres

*_Iosbase*<br/>
Objet `ios_base`.

### <a name="remarks"></a>Notes

Le manipulateur appelle _I `osbase.`[ios_base::unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`, puis retourne _I `osbase`.

## <a name="fixed"></a>  fixed

Indique qu'un nombre à virgule flottante est affiché en notation décimale fixe.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

`fixed` est la notation d’affichage par défaut pour les nombres à virgule flottante. [scientific](../standard-library/ios-functions.md#scientific) fait en sorte que les nombres à virgule flottante soient affichés à l’aide de la notation scientifique.

Le manipulateur appelle * str.*[setf](../standard-library/ios-base-class.md#setf)( `ios_base::fixed`, `ios_base::floatfield`), puis retourne *str*.

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

## <a name="hex"></a>  hex

Indique que les variables de type entier sont affichées en notation de base 16.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, les variables de type entier sont affichées en notation de base 10. [dec](../standard-library/ios-functions.md#dec) et [oct](../standard-library/ios-functions.md#oct) modifient également le mode d’affichage des variables de type entier.

Le manipulateur appelle `str` **.** [setf](../standard-library/ios-base-class.md#setf)( `ios_base::hex`, `ios_base::basefield`), puis retourne *str*.

### <a name="example"></a>Exemple

Consultez [dec](../standard-library/ios-functions.md#dec) pour obtenir un exemple montrant comment utiliser `hex`.

## <a name="internal"></a>  internal

Aligne à gauche le signe d'un nombre et aligne à droite le nombre.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet à partir de laquelle *str* est dérivée.

### <a name="remarks"></a>Notes

[showpos](../standard-library/ios-functions.md#showpos) provoque l’affichage du signe pour les nombres positifs.

Le manipulateur appelle `str`. [SETF](../standard-library/ios-base-class.md#setf)( [ios_base::internal](../standard-library/ios-base-class.md#fmtflags), [ios_base::adjustfield](../standard-library/ios-base-class.md#fmtflags)), puis retourne *str*.

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

## <a name="left"></a>  left

Fait en sorte que le texte qui n'est pas aussi large que la largeur de sortie apparaisse dans le flux aligné avec la marge de gauche.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::left`, `ios_base::adjustfield`), puis retourne *str*.

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

## <a name="noboolalpha"></a>  noboolalpha

Indique que les variables de type [bool](../cpp/bool-cpp.md) apparaissent comme 1 ou 0 dans le flux.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, `noboolalpha` est activé.

`noboolalpha` appelle `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::boolalpha`), puis retourne *str*.

[boolalpha](../standard-library/ios-functions.md#boolalpha) inverse l’effet de `noboolalpha`.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `noboolalpha`, consultez [boolalpha](../standard-library/ios-functions.md#boolalpha).

## <a name="noshowbase"></a>  noshowbase

Désactive l'indication de la base de notation dans laquelle un nombre est affiché.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

`noshowbase` est activé par défaut. Utilisez [showbase](../standard-library/ios-functions.md#showbase) pour indiquer la base notationnelle des nombres.

Le manipulateur appelle `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showbase`), puis retourne *str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `noshowbase`, consultez [showbase](../standard-library/ios-functions.md#showbase).

## <a name="noshowpoint"></a>  noshowpoint

Affiche uniquement la partie entière des nombres à virgule flottante dont la partie fractionnaire est égale à zéro.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

`noshowpoint` est activé par défaut. Utilisez [showpoint](../standard-library/ios-functions.md#showpoint) et [precision](../standard-library/ios-base-class.md#precision) pour afficher les zéros non significatifs après la virgule décimale.

Le manipulateur appelle `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showpoint`), puis retourne *str*.

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

## <a name="noshowpos"></a>  noshowpos

Fait en sorte que les nombres positifs ne soient pas signés explicitement.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

`noshowpos` est activé par défaut.

Le manipulateur appelle `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showps`), puis retourne *str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `noshowpos`, consultez [showpos](../standard-library/ios-functions.md#showpos).

## <a name="noskipws"></a>  noskipws

Fait en sorte que les espaces soient lus par le flux d'entrée.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, [skipws](../standard-library/ios-functions.md#skipws) est activé. La lecture d’un espace dans le flux d’entrée signale la fin de la mémoire tampon.

Le manipulateur appelle `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::skipws`), puis retourne *str*.

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

## <a name="nounitbuf"></a>  nounitbuf

Fait en sorte que la sortie soit mise en mémoire tampon et traitée quand la mémoire tampon est pleine.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

[unitbuf](../standard-library/ios-functions.md#unitbuf) fait en sorte que la mémoire tampon soit traitée quand elle n’est pas vide.

Le manipulateur appelle `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::unitbuf`), puis retourne *str*.

## <a name="nouppercase"></a>  nouppercase

Spécifie que les chiffres hexadécimaux et l'exposant en notation scientifique apparaissent en minuscules.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Le manipulateur appelle `str`.[ unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::uppercase`), puis retourne *str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `nouppercase`, consultez [uppercase](../standard-library/ios-functions.md#uppercase).

## <a name="oct"></a>  oct

Indique que les variables de type entier sont affichées en notation de base 8.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet à partir de laquelle *str* est dérivée.

### <a name="remarks"></a>Notes

Par défaut, les variables de type entier sont affichées en notation de base 10. [dec](../standard-library/ios-functions.md#dec) et [hex](../standard-library/ios-functions.md#hex) modifient également le mode d’affichage des variables de type entier.

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::oct`, `ios_base::basefield`), puis retourne *str*.

### <a name="example"></a>Exemple

Consultez [dec](../standard-library/ios-functions.md#dec) pour obtenir un exemple montrant comment utiliser `oct`.

## <a name="right"></a>  right

Fait en sorte que le texte qui n'est pas aussi large que la largeur de sortie apparaisse dans le flux aligné avec la marge de droite.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet à partir de laquelle *str* est dérivée.

### <a name="remarks"></a>Notes

[left](../standard-library/ios-functions.md#left) modifie également la justification du texte.

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::right`, `ios_base::adjustfield`), puis retourne *str*.

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

## <a name="scientific"></a>  scientific

Fait en sorte que les nombres à virgule flottante soient affichés à l’aide de la notation scientifique.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, la notation [fixed](../standard-library/ios-functions.md#fixed) est appliquée pour les nombres à virgule flottante.

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::scientific`, `ios_base::floatfield`), puis retourne *str*.

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

## <a name="showbase"></a>  showbase

Indique la base de notation dans laquelle un nombre est affiché.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

La base notationnelle d’un nombre significatif peut être modifiée avec [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct) ou [hex](../standard-library/ios-functions.md#hex).

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showbase`), puis retourne *str*.

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

## <a name="showpoint"></a>  showpoint

Affiche la partie entière d'un nombre à virgule flottante et les chiffres à droite de la virgule décimale même quand la partie fractionnaire est égale à zéro.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, [noshowpoint](../standard-library/ios-functions.md#noshowpoint) est activé.

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showpoint`), puis retourne *str*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `showpoint`, consultez [noshowpoint](../standard-library/ios-functions.md#noshowpoint).

## <a name="showpos"></a>  showpos

Fait en sorte que les nombres positifs soient signés explicitement.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

[noshowpos](../standard-library/ios-functions.md#noshowpos) est la valeur par défaut.

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showpos`), puis retourne *str*.

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

## <a name="skipws"></a>  skipws

Fait en sorte que les espaces ne soient pas lus par le flux d'entrée.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet à partir duquel _ *Str* est dérivé.

### <a name="remarks"></a>Notes

Par défaut, `skipws` est activé. [noskipws](../standard-library/ios-functions.md#noskipws) fait en sorte que les espaces soient lus à partir du flux d’entrée.

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::skipws`), puis retourne *str*.

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

```Output

1 2 3

```

```Output

      1 2 3.1.
.2.
.3.
```

## <a name="unitbuf"></a>  unitbuf

Fait en sorte que la sortie soit traitée quand la mémoire tampon n'est pas vide.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet à partir de laquelle *str* est dérivée.

### <a name="remarks"></a>Notes

Notez que `endl` vide aussi la mémoire tampon.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) est activé par défaut.

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( [ios_base::unitbuf](../standard-library/ios-base-class.md#fmtflags)), puis retourne *str*.

## <a name="uppercase"></a>  uppercase

Spécifie que les chiffres hexadécimaux et l'exposant en notation scientifique apparaissent en majuscules.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Référence à un objet de type [ios_base](../standard-library/ios-base-class.md), ou à un type qui hérite de `ios_base`.

### <a name="return-value"></a>Valeur de retour

Une référence à l’objet à partir de laquelle *str* est dérivée.

### <a name="remarks"></a>Notes

Par défaut, [nouppercase](../standard-library/ios-functions.md#nouppercase) est activé.

Le manipulateur appelle `str`.[ SETF](../standard-library/ios-base-class.md#setf)( [ios_base::uppercase](../standard-library/ios-base-class.md#fmtflags)), puis retourne *str*.

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

## <a name="see-also"></a>Voir aussi

[\<ios>](../standard-library/ios.md)<br/>
