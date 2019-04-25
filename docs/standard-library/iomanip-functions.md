---
title: '&lt;iomanip&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::get_money
- iomanip/std::get_time
- iomanip/std::put_money
- iomanip/std::put_time
- iomanip/std::quoted
- iomanip/std::resetiosflags
- iomanip/std::setbase
- iomanip/std::setfill
- iomanip/std::setiosflags
- iomanip/std::setprecision
- iomanip/std::setw
ms.assetid: 3ddde610-70cc-4cfa-8a89-3e83d1d356a8
helpviewer_keywords:
- std::get_money [C++]
- std::get_time [C++]
- std::put_money [C++]
- std::put_time [C++]
- std::quoted [C++]
- std::resetiosflags [C++]
- std::setbase [C++]
- std::setfill [C++]
- std::setiosflags [C++]
- std::setprecision [C++]
- std::setw [C++]
ms.openlocfilehash: b5ead8b1000fd6c2708b2450f71da3dc612dc51d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158558"
---
# <a name="ltiomanipgt-functions"></a>&lt;iomanip&gt;, fonctions

||||
|-|-|-|
|[get_money](#iomanip_get_money)|[get_time](#iomanip_get_time)|[put_money](#iomanip_put_money)|
|[put_time](#iomanip_put_time)|[quoted](#quoted)|[resetiosflags](#resetiosflags)|
|[setbase](#setbase)|[setfill](#setfill)|[setiosflags](#setiosflags)|
|[setprecision](#setprecision)|[setw](#setw)|

## <a name="iomanip_get_money"></a>  get_money

Extrait une valeur monétaire à partir d’un flux en utilisant le format souhaité, et retourne la valeur dans un paramètre.

```cpp
template <class Money>
T7 get_money(Money& _Amount, bool _Intl);
```

### <a name="parameters"></a>Paramètres

*_Amount*<br/>
Valeur monétaire extraite.

*_Intl*<br/>
Si **true**, utiliser le format international. La valeur par défaut est **false**.

### <a name="remarks"></a>Notes

Le manipulateur retourne un objet qui, quand il est extrait à partir du flux `str`, se comporte comme un `formatted input function` qui appelle la fonction membre `get` pour la facette de paramètres régionaux `money_get` associés `str`, à l’aide *_ Intl* pour indiquer le format international. Si réussie, l’appel stocke dans *_quantité* la valeur monétaire extraite. Le manipulateur retourne ensuite `str`.

`Money` doit être de type `long double` ou une instanciation de `basic_string` avec le même élément et les mêmes paramètres de caractéristiques que `str`.

## <a name="iomanip_get_time"></a>  get_time

Extrait une valeur de temps à partir d’un flux à l’aide du format souhaité. Retourne la valeur dans un paramètre en tant que structure de temps.

```cpp
template <class Elem>
T10 put_time(struct tm *_Tptr, const Elem *_Fmt);
```

### <a name="parameters"></a>Paramètres

*_Tptr*<br/>
Heure sous la forme d’une structure de temps.

*_Fmt*<br/>
Format à utiliser pour obtenir la valeur de temps.

### <a name="remarks"></a>Notes

Le manipulateur retourne un objet qui, quand il est extrait à partir du flux `str`, se comporte comme un `formatted input function` qui appelle la fonction membre `get` pour la facette de paramètres régionaux `time_get` associée à `str`, en utilisant `tptr` pour indiquer la structure de temps et `fmt` pour indiquer le début d’une chaîne de format terminée par un caractère Null. En cas de réussite, l’appel stocke dans la structure de temps les valeurs associées à tous les champs de temps extraits. Le manipulateur retourne ensuite `str`.

## <a name="iomanip_put_money"></a>  put_money

Insère une valeur monétaire dans un flux en utilisant le format souhaité.

```cpp
template <class Money>
T8 put_money(const Money& _Amount, bool _Intl);
```

### <a name="parameters"></a>Paramètres

*_Amount*<br/>
Valeur monétaire à insérer dans le flux.

*_Intl*<br/>
La valeur **true** si le manipulateur doit utiliser le format international, **false** si il ne doit pas.

### <a name="return-value"></a>Valeur de retour

Retourne `str`.

### <a name="remarks"></a>Notes

Le manipulateur retourne un objet qui, quand il est inséré dans le flux `str`, se comporte comme une fonction de sortie mise en forme qui appelle la fonction membre `put` pour la facette de paramètres régionaux `money_put` associée à `str`. Si la réussite, l’appel insère `amount` correctement mis en forme, à l’aide de * _Intl` to indicate international format and `str.fill()`, as the fill element. The manipulator then returns `str'.

`Money` doit être de type `long double` ou une instanciation de `basic_string` avec le même élément et les mêmes paramètres de caractéristiques que `str`.

## <a name="iomanip_put_time"></a>  put_time

Écrit une valeur de temps à partir d’une structure de temps dans un flux à l’aide d’un format spécifié.

```cpp
template <class Elem>
T10 put_time(struct tm* _Tptr, const Elem* _Fmt);
```

### <a name="parameters"></a>Paramètres

*_Tptr*<br/>
Valeur de temps à écrire dans le flux, fournie dans une structure de temps.

*_Fmt*<br/>
Format à utiliser pour écrire la valeur de temps.

### <a name="remarks"></a>Notes

Le manipulateur retourne un objet qui, quand il est inséré dans le flux `str`, se comporte comme un `formatted output function`. La fonction de sortie appelle la fonction membre `put` pour la facette de paramètres régionaux `time_put` associée à `str`. Utilise la fonction de sortie *_Tptr* pour indiquer la structure de temps et *_Fmt* pour indiquer le début d’une chaîne de format se terminant par null. En cas de réussite, l’appel insère le texte littéral à partir de la chaîne de format et les valeurs converties à partir de la structure de temps. Le manipulateur retourne ensuite `str`.

## <a name="quoted"></a>  quoted

**(Nouveauté dans C++14)** Manipulateur iostream qui permet d’effectuer facilement un aller-retour de chaînes dans et hors de flux à l’aide des opérateurs >> et <<.

```cpp
quoted(std::string str) // or wstring
quoted(const char* str) //or wchar_t*
quoted(std::string str, char delimiter, char escape) // or wide versions
quoted(const char* str, char delimiter, char escape) // or wide versions
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Un std::string, un char\*, chaîne de littéral de chaîne brut ou littéral ou une version large d’un de ces (par exemple, std::wstring, wchar_t\*).

*delimiter*<br/>
Caractère spécifié par l'utilisateur ou caractère large à utiliser comme délimiteur de début et de fin de chaîne.

*escape*<br/>
Caractère spécifié par l'utilisateur ou caractère large à utiliser comme caractère d'échappement pour les séquences d'échappement dans la chaîne.

### <a name="remarks"></a>Notes

Consultez [Utilisation des opérateurs d’insertion et contrôle du format](../standard-library/using-insertion-operators-and-controlling-format.md).

### <a name="example"></a>Exemple

Cet exemple montre comment utiliser `quoted` avec le délimiteur et le caractère d'échappement par défaut avec des chaînes étroites. Les chaînes larges sont également prises en charge.

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_quoted_v_nonquoted()
{
    // Results are identical regardless of input string type:
    // string inserted { R"(This is a "sentence".)" }; // raw string literal
    // string inserted { "This is a \"sentence\"." };  // regular string literal
    const char* inserted = "This is a \"sentence\".";  // const char*
    stringstream ss, ss_quoted;
    string extracted, extracted_quoted;

    ss << inserted;
    ss_quoted << quoted(inserted);

    cout << "ss.str() is storing       : " << ss.str() << endl;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl << endl;

    // Round-trip the strings
    ss >> extracted;
    ss_quoted >> quoted(extracted_quoted);

    cout << "After round trip: " << endl;
    cout << "Non-quoted      : " << extracted << endl;
    cout << "Quoted          : " << extracted_quoted << endl;
}

void main(int argc, char* argv[])
{
    show_quoted_v_nonquoted();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}

/* Output:
ss.str() is storing       : This is a "sentence".
ss_quoted.str() is storing: "This is a \"sentence\"."

After round trip:
Non-quoted      : This
Quoted          : This is a "sentence".

Press Enter to exit
*/
```

### <a name="example"></a>Exemple

L'exemple suivant montre comment fournir un délimiteur et/ou un caractère d'échappement personnalisé :

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_custom_delimiter()
{
    string inserted{ R"("This" "is" "a" "heavily-quoted" "sentence".)" };
    // string inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    // const char* inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    stringstream ss, ss_quoted;
    string extracted;

    ss_quoted << quoted(inserted, '*');
    ss << inserted;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl;
    cout << "ss.str() is storing       : " << ss.str() << endl << endl;

    // Use the same quoted arguments as on insertion.
    ss_quoted >> quoted(extracted, '*');

    cout << "After round trip: " << endl;
    cout << "Quoted          : " << extracted << endl;

    extracted = {};
    ss >> extracted;
    cout << "Non-quoted      : " << extracted << endl << endl;
}

void show_custom_escape()
{
    string inserted{ R"(\\root\trunk\branch\nest\egg\yolk)" };
    // string inserted{ "\\\\root\\trunk\\branch\\nest\\egg\\yolk" };
    stringstream ss, ss_quoted, ss_quoted_custom;
    string extracted;

    // Use '"' as delimiter and '~' as escape character.
    ss_quoted_custom << quoted(inserted, '"', '~');
    ss_quoted << quoted(inserted);
    ss << inserted;
    cout << "ss_quoted_custom.str(): " << ss_quoted_custom.str() << endl;
    cout << "ss_quoted.str()       : " << ss_quoted.str() << endl;
    cout << "ss.str()              : " << ss.str() << endl << endl;

    // No spaces in this string, so non-quoted behaves same as quoted
    // after round-tripping.
}

void main(int argc, char* argv[])
{
    cout << "Custom delimiter:" << endl;
    show_custom_delimiter();
    cout << "Custom escape character:" << endl;
    show_custom_escape();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}
/* Output:
Custom delimiter:
ss_quoted.str() is storing: *"This" "is" "a" "heavily-quoted" "sentence".*
ss.str() is storing       : "This" "is" "a" "heavily-quoted" "sentence".

After round trip:
Quoted          : "This" "is" "a" "heavily-quoted" "sentence".
Non-quoted      : "This"

Custom escape character:
ss_quoted_custom.str(): "\\root\trunk\branch\nest\egg\yolk"
ss_quoted.str()       : "\\\\root\\trunk\\branch\\nest\\egg\\yolk"
ss.str()              : \\root\trunk\branch\nest\egg\yolk

Press Enter to exit
*/
```

## <a name="resetiosflags"></a>  resetiosflags

Efface les indicateurs spécifiés.

```cpp
T1 resetiosflags(ios_base::fmtflags Mask);
```

### <a name="parameters"></a>Paramètres

*Masque*<br/>
Indicateurs à effacer.

### <a name="return-value"></a>Valeur de retour

Le manipulateur retourne un objet qui, lors de l’extrait ou inséré dans le flux `str`, appels **str**. [SETF](../standard-library/ios-base-class.md#setf)( `ios_base::` [fmtflags](../standard-library/ios-base-class.md#fmtflags), _ *masque*), puis retourne `str`.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `resetiosflags`, consultez [setw](../standard-library/iomanip-functions.md#setw).

## <a name="setbase"></a>  setbase

Définir la base pour les entiers.

```cpp
T3 setbase(int _Base);
```

### <a name="parameters"></a>Paramètres

*_Base*<br/>
Base numérique.

### <a name="return-value"></a>Valeur de retour

Le manipulateur retourne un objet qui, lors de l’extrait ou inséré dans le flux `str`, appels **str**. `setf`( **masque**, [ios_base::basefield](../standard-library/ios-base-class.md#fmtflags)), puis retourne `str`. Ici, `mask` est déterminée comme suit :

- Si _ *Base* est 8, puis `mask` est `ios_base::` [oct](../standard-library/ios-functions.md#oct).

- Si _ *Base* est 10, mask est `ios_base::`[dec](../standard-library/ios-functions.md#dec).

- Si _ *Base* est 16, puis `mask` est `ios_base::` [hexadécimal](../standard-library/ios-functions.md#hex).

- Si _ *Base* est une autre valeur, mask est `ios_base::`[fmtflags](../standard-library/ios-base-class.md#fmtflags)(0).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `setbase`, consultez [setw](../standard-library/iomanip-functions.md#setw).

## <a name="setfill"></a>  setfill

Définit le caractère qui sera utilisé pour remplir les espaces dans un affichage aligné à droite.

```cpp
template <class Elem>
T4 setfill(Elem Ch);
```

### <a name="parameters"></a>Paramètres

*Ch*<br/>
Caractère qui sera utilisé pour remplir les espaces dans un affichage aligné à droite.

### <a name="return-value"></a>Valeur de retour

Le manipulateur de modèle retourne un objet qui, quand extrait ou inséré dans le flux `str`, appels **str**. [remplissage](../standard-library/basic-ios-class.md#fill)(`Ch`), puis retourne `str`. Le type `Elem` doit être le même que le type d’élément pour le flux `str`.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `setfill`, consultez [setw](../standard-library/iomanip-functions.md#setw).

## <a name="setiosflags"></a>  setiosflags

Définit les indicateurs spécifiés.

```cpp
T2 setiosflags(ios_base::fmtflags Mask);
```

### <a name="parameters"></a>Paramètres

*Masque*<br/>
Indicateurs à définir.

### <a name="return-value"></a>Valeur de retour

Le manipulateur retourne un objet qui, lors de l’extrait ou inséré dans le flux `str`, appels **str**. [SETF](../standard-library/ios-base-class.md#setf)(_ *masque*), puis retourne `str`.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `setiosflags`, consultez [setw](../standard-library/iomanip-functions.md#setw).

## <a name="setprecision"></a>  setprecision

Définit la précision des valeurs à virgule flottante.

```cpp
T5 setprecision(streamsize Prec);
```

### <a name="parameters"></a>Paramètres

*PREC*<br/>
Précision des valeurs à virgule flottante.

### <a name="return-value"></a>Valeur de retour

Le manipulateur retourne un objet qui, lors de l’extrait ou inséré dans le flux `str`, appels **str**. [précision](../standard-library/ios-base-class.md#precision)(`Prec`), puis retourne `str`.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `setprecision`, consultez [setw](../standard-library/iomanip-functions.md#setw).

## <a name="setw"></a>  setw

Spécifie la largeur du champ affichage pour l’élément suivant dans le flux.

```cpp
T6 setw(streamsize Wide);
```

### <a name="parameters"></a>Paramètres

*Wide*<br/>
Largeur de la zone d’affichage.

### <a name="return-value"></a>Valeur de retour

Le manipulateur retourne un objet qui, lors de l’extrait ou inséré dans le flux `str`, appels **str**. [largeur](../standard-library/ios-base-class.md#width)(_ *large*), puis retourne `str`.

### <a name="remarks"></a>Notes

setw définit la largeur uniquement pour l’élément suivant dans le flux et doit être inséré avant chaque élément dont vous souhaitez spécifier la largeur.

### <a name="example"></a>Exemple

```cpp
// iomanip_setw.cpp
// compile with: /EHsc
// Defines the entry point for the console application.
//
// Sample use of the following manipulators:
//   resetiosflags
//   setiosflags
//   setbase
//   setfill
//   setprecision
//   setw

#include <iostream>
#include <iomanip>

using namespace std;

const double   d1 = 1.23456789;
const double   d2 = 12.3456789;
const double   d3 = 123.456789;
const double   d4 = 1234.56789;
const double   d5 = 12345.6789;
const long      l1 = 16;
const long      l2 = 256;
const long      l3 = 1024;
const long      l4 = 4096;
const long      l5 = 65536;
int         base = 10;

void DisplayDefault( )
{
   cout << endl << "default display" << endl;
   cout << "d1 = " << d1 << endl;
   cout << "d2 = " << d2 << endl;
   cout << "d3 = " << d3 << endl;
   cout << "d4 = " << d4 << endl;
   cout << "d5 = " << d5 << endl;
}

void DisplayWidth( int n )
{
   cout << endl << "fixed width display set to " << n << ".\n";
   cout << "d1 = " << setw(n) << d1 << endl;
   cout << "d2 = " << setw(n) << d2 << endl;
   cout << "d3 = " << setw(n) << d3 << endl;
   cout << "d4 = " << setw(n) << d4 << endl;
   cout << "d5 = " << setw(n) << d5 << endl;
}

void DisplayLongs( )
{
   cout << setbase(10);
   cout << endl << "setbase(" << base << ")" << endl;
   cout << setbase(base);
   cout << "l1 = " << l1 << endl;
   cout << "l2 = " << l2 << endl;
   cout << "l3 = " << l3 << endl;
   cout << "l4 = " << l4 << endl;
   cout << "l5 = " << l5 << endl;
}

int main( int argc, char* argv[] )
{
   DisplayDefault( );

   cout << endl << "setprecision(" << 3 << ")" << setprecision(3);
   DisplayDefault( );

   cout << endl << "setprecision(" << 12 << ")" << setprecision(12);
   DisplayDefault( );

   cout << setiosflags(ios_base::scientific);
   cout << endl << "setiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << resetiosflags(ios_base::scientific);
   cout << endl << "resetiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << endl << "setfill('" << 'S' << "')" << setfill('S');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setfill('" << ' ' << "')" << setfill(' ');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setprecision(" << 8 << ")" << setprecision(8);
   DisplayWidth(10);
   DisplayDefault( );

   base = 16;
   DisplayLongs( );

   base = 8;
   DisplayLongs( );

   base = 10;
   DisplayLongs( );

   return   0;
}
```

```Output

default display
d1 = 1.23457
d2 = 12.3457
d3 = 123.457
d4 = 1234.57
d5 = 12345.7

setprecision(3)
default display
d1 = 1.23
d2 = 12.3
d3 = 123
d4 = 1.23e+003
d5 = 1.23e+004

setprecision(12)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setiosflags(4096)
default display
d1 = 1.234567890000e+000
d2 = 1.234567890000e+001
d3 = 1.234567890000e+002
d4 = 1.234567890000e+003
d5 = 1.234567890000e+004

resetiosflags(4096)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill('S')
fixed width display set to 15.
d1 = SSSSS1.23456789
d2 = SSSSS12.3456789
d3 = SSSSS123.456789
d4 = SSSSS1234.56789
d5 = SSSSS12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill(' ')
fixed width display set to 15.
d1 =      1.23456789
d2 =      12.3456789
d3 =      123.456789
d4 =      1234.56789
d5 =      12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setprecision(8)
fixed width display set to 10.
d1 =  1.2345679
d2 =  12.345679
d3 =  123.45679
d4 =  1234.5679
d5 =  12345.679

default display
d1 = 1.2345679
d2 = 12.345679
d3 = 123.45679
d4 = 1234.5679
d5 = 12345.679

setbase(16)
l1 = 10
l2 = 100
l3 = 400
l4 = 1000
l5 = 10000

setbase(8)
l1 = 20
l2 = 400
l3 = 2000
l4 = 10000
l5 = 200000

setbase(10)
l1 = 16
l2 = 256
l3 = 1024
l4 = 4096
l5 = 65536
```

## <a name="see-also"></a>Voir aussi

[\<iomanip>](../standard-library/iomanip.md)<br/>
