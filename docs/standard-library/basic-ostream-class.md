---
title: basic_ostream, classe
ms.date: 03/27/2019
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
ms.openlocfilehash: 972c21feec805e4c1032f0ebad1e3ac0d7daa7dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219233"
---
# <a name="basic_ostream-class"></a>basic_ostream, classe

Ce modèle de classe décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux avec des éléments de type `Elem` , également appelés [char_type](../standard-library/basic-ios-class.md#char_type), dont les caractéristiques sont déterminées par la classe `Tr` , également appelée [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Elem*\
`char_type`

*TR*\
`traits_type` du caractère.

## <a name="remarks"></a>Notes

La plupart des fonctions membres qui surchargent [operator<<](#basic_ostream_operator_lt_lt) sont des fonctions de sortie mises en forme. Elles suivent le modèle :

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{try
{<convert and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
width(0);
// Except for operator<<(Elem)
setstate(state);

return (*this);
```

Deux autres fonctions membres sont des fonctions de sortie non mises en forme. Elles suivent le modèle :

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (!ok)
    state |= badbit;
else
{try
{<obtain and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
setstate(state);

return (*this);
```

Les deux groupes de fonctions appellent [SetState](../standard-library/basic-ios-class.md#setstate)(**badbit**) s’ils rencontrent un échec lors de l’insertion d’éléments.

Un objet de classe basic_istream \< **Elem**, **Tr**> stocke uniquement un objet de base public virtuel de la classe [basic_ios](../standard-library/basic-ios-class.md) **\<Elem**, **Tr>** .

## <a name="example"></a>Exemple

Pour en savoir plus sur les flux de sortie, consultez l’exemple relatif à [basic_ofstream, classe](../standard-library/basic-ofstream-class.md).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_ostream](#basic_ostream)|Construit un objet `basic_ostream`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[postconsommation](#flush)|Vide la mémoire tampon.|
|[posé](#put)|Place un caractère dans un flux.|
|[seekp](#seekp)|Réinitialise la position dans le flux de sortie.|
|[sentry](#sentry)|La classe imbriquée décrit un objet dont la déclaration structure les fonctions de sortie mise en forme et les fonctions de sortie non mise en forme.|
|[swap](#swap)|Échange les valeurs de cet objet `basic_ostream` avec celles de l'objet `basic_ostream` fourni.|
|[tellp](#tellp)|Indique la position dans le flux de sortie.|
|[Ecrire](#write)|Place des caractères dans un flux.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#op_eq)|Affecte la valeur du paramètre d'objet `basic_ostream` fourni à cet objet.|
|[<<d’opérateur](#basic_ostream_operator_lt_lt)|Écrit dans le flux.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<ostream>

**Espace de noms :** std

## <a name="basic_ostreambasic_ostream"></a><a name="basic_ostream"></a>basic_ostream :: basic_ostream

Construit un objet `basic_ostream`.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Paramètres

*strbuf*\
Objet de type [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**`true`** s’il s’agit d’un flux standard ; Sinon, **`false`** .

*Oui*\
Référence rvalue à un objet de type `basic_ostream`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant [init](../standard-library/basic-ios-class.md#init)( `strbuf` ). Le deuxième constructeur initialise la classe de base en appelant [basic_ios :: Move](../standard-library/basic-ios-class.md#move) `(right)` .

### <a name="example"></a>Exemple

Pour en savoir plus sur les flux de sortie, consultez l’exemple relatif à [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

## <a name="basic_ostreamflush"></a><a name="flush"></a>basic_ostream :: Flush

Vide la mémoire tampon.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

Si [rdbuf](../standard-library/basic-ios-class.md#rdbuf) n’est pas un pointeur null, la fonction membre appelle **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#pubsync). Si le résultat est -1, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Elle retourne ** \* This**.

### <a name="example"></a>Exemple

```cpp
// basic_ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "test";
   cout.flush();
}
```

```Output
test
```

## <a name="basic_ostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt"></a>basic_ostream ::, opérateur&lt;&lt;

Écrit dans le flux.

```cpp
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

### <a name="parameters"></a>Paramètres

*PFN*\
Pointeur de fonction.

*strbuf*\
Pointeur vers un objet `stream_buf`.

*multiples*\
Élément à écrire dans le flux.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

L’en-tête \<ostream> définit également plusieurs opérateurs d’insertion globaux. Pour plus d’informations, consultez [opérateur<<](../standard-library/ostream-operators.md#op_lt_lt).

La première fonction membre garantit qu’une expression du formulaire `ostr << endl` appelle [Endl](../standard-library/ostream-functions.md#endl)**(OSTR)**, puis retourne ** \* This**. Les deuxième et troisième fonctions garantissent que d’autres manipulateurs, comme [hex](../standard-library/ios-functions.md#hex), se comportent de la même façon. Les fonctions restantes sont toutes les fonctions de sortie mises en forme.

La fonction

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

extrait des éléments de *strbuf*, si *strbuf* n’est pas un pointeur null, et les insère. L’extraction s’arrête à la fin du fichier ou si une extraction lève une exception (qui est à nouveau levée). Elle s’arrête également, sans extraire l’élément en question, si une insertion échoue. Si la fonction n’insère aucun élément ou si une extraction lève une exception, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Dans tous les cas, la fonction retourne ** \* This**.

La fonction

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

convertit en `_Val` champ booléen et l’insère en appelant [use_facet](../standard-library/basic-filebuf-class.md#open) **<num_put \<Elem, OutIt> ** `(` [getloc](../standard-library/ios-base-class.md#getloc)). [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**). Ici, `OutIt` est défini en tant que [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md) **\<Elem, Tr>** . La fonction retourne ** \* This**.

Les fonctions

```cpp
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

chaque convertit *Val* en un champ numérique et l’insère en appelant **use_facet \<Elem, OutIt><num_put**( `getloc` ). **put**(**outlt**( `rdbuf` ), ** \* This**, `getloc` , **Val**). Ici, **outlt** est défini en tant que **ostreambuf_iterator \<Elem, Tr> **. La fonction retourne ** \* This**.

Les fonctions

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

chaque instruction Convert *Val* dans un champ numérique et l’insère en appelant **use_facet<\<Elem, OutIt> num_put**( `getloc` )**. put**(**outlt**( `rdbuf` ), ** \* This**, `getloc` , **Val**). Ici, **outlt** est défini en tant que **ostreambuf_iterator \<Elem, Tr> **. La fonction retourne ** \* This**.

### <a name="example"></a>Exemple

```cpp
// basic_ostream_op_write.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```

## <a name="basic_ostreamoperator"></a><a name="op_eq"></a>basic_ostream :: Operator =

Attribue la valeur du paramètre d’objet `basic_ostream` fourni à cet objet.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence `rvalue` à un objet `basic_ostream`.

### <a name="remarks"></a>Notes

L’opérateur membre appelle swap `(right)`.

## <a name="basic_ostreamput"></a><a name="put"></a>basic_ostream ::p ut

Place un caractère dans un flux.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Paramètres

*_Ch*\
Un caractère.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

La fonction de sortie non mise en forme insère l’élément *_Ch*. Elle retourne ** \* This**.

### <a name="example"></a>Exemple

```cpp
// basic_ostream_put.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout.put( 'v' );
   cout << endl;
   wcout.put( L'l' );
}
```

```Output
v
l
```

## <a name="basic_ostreamseekp"></a><a name="seekp"></a>basic_ostream :: seekp

Réinitialise la position dans le flux de sortie.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Paramètres

*_Pos*\
Position dans le flux.

*_Off*\
Décalage par rapport à *_Way*.

*_Way*\
Une des énumérations [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

En cas d' [échec](../standard-library/basic-ios-class.md#fail) **`false`** , la première fonction membre appelle **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), pour certains `pos_type` objets temporaires `newpos` . Si `fail` a la valeur false, la deuxième fonction appelle **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_OFF, _Way*). Dans les deux cas, si ( `off_type` )**newpos = =** ( `off_type` ) (-1) (l’opération de positionnement échoue), la fonction appelle **ISTR.** [SetState](../standard-library/basic-ios-class.md#setstate)(**failbit**). Les deux fonctions retournent ** \* This**.

### <a name="example"></a>Exemple

```cpp
// basic_ostream_seekp.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main()
{
    using namespace std;
    ofstream x("basic_ostream_seekp.txt");
    streamoff i = x.tellp();
    cout << i << endl;
    x << "testing";
    i = x.tellp();
    cout << i << endl;
    x.seekp(2);   // Put char in third char position in file
    x << " ";

    x.seekp(2, ios::end);   // Put char two after end of file
    x << "z";
}
```

```Output
0
7
```

## <a name="basic_ostreamsentry"></a><a name="sentry"></a>basic_ostream :: Sentry

La classe imbriquée décrit un objet dont la déclaration structure les fonctions de sortie mise en forme et les fonctions de sortie non mise en forme.

classe Sentry {public : Explicit Sentry (basic_ostream \<Elem, Tr>& _Ostr); opérateur bool () const ; ~ Sentry ();};

### <a name="remarks"></a>Notes

La classe imbriquée décrit un objet dont la déclaration structure les fonctions de sortie mise en forme et les fonctions de sortie non mise en forme. Si **OSTR.** [bonne](../standard-library/basic-ios-class.md#good) est **`true`** et **OSTR.** l' [égalité](../standard-library/basic-ios-class.md#tie) n’est pas un pointeur null, le constructeur appelle **OSTR. tie->** [vidage](#flush). Le constructeur stocke ensuite la valeur retournée par `ostr.good` dans `status` . Un appel ultérieur à `operator bool` remet cette valeur stockée.

Si `uncaught_exception` retourne **`false`** et [Flags](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) est différent de zéro, le destructeur appelle [flush](#flush).

## <a name="basic_ostreamswap"></a><a name="swap"></a>basic_ostream :: swap

Échange les valeurs de cet objet `basic_ostream` avec celles du `basic_ostream` fourni.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence à un objet `basic_ostream`.

### <a name="remarks"></a>Notes

La fonction membre appelle [basic_ios :: swap](../standard-library/basic-ios-class.md#swap) `(right)` pour échanger le contenu de cet objet pour le contenu de *Right*.

## <a name="basic_ostreamtellp"></a><a name="tellp"></a>basic_ostream :: tellp

Signale la position dans le flux de sortie.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Valeur de retour

Position dans le flux de sortie.

### <a name="remarks"></a>Notes

En cas d' [échec](../standard-library/basic-ios-class.md#fail) **`false`** , la fonction membre retourne [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur` , **in**). Sinon, elle retourne `pos_type`(-1).

### <a name="example"></a>Exemple

Consultez [seekp](#seekp) pour obtenir un exemple d’utilisation de `tellp`.

## <a name="basic_ostreamwrite"></a><a name="write"></a>basic_ostream :: Write

Place des caractères dans un flux.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre de caractères à placer dans le flux.

*Str*\
Caractères à placer dans le flux.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

La [fonction de sortie non mise en forme](../standard-library/basic-ostream-class.md) insère la séquence d’éléments *Count* à partir de *Str*.

### <a name="example"></a>Exemple

Consultez [streamsize](../standard-library/ios-typedefs.md#streamsize) pour obtenir un exemple d’utilisation de `write`.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
