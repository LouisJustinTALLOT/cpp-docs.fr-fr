---
title: basic_istream, classe
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: 03a6e3a65d6dc8c2fa896949855bd23a01578e5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376827"
---
# <a name="basic_istream-class"></a>basic_istream, classe

Décrit un objet qui contrôle l’extraction d’éléments et d’objets codés à partir d’une mémoire tampon de flux avec des éléments de type `Char_T`, également appelé [char_type](../standard-library/basic-ios-class.md#char_type), dont les caractéristiques sont déterminées par la classe *Tr*, également appelée [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>Notes

La plupart des fonctions membres qui surchargent [operator>>](#op_gt_gt) sont des fonctions d’entrée mises en forme. Elles suivent le modèle :

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

De nombreuses autres fonctions membres sont des fonctions d'entrée non mise en forme. Elles suivent le modèle :

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

Les deux groupes [`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` de fonctions appellent s’ils rencontrent la fin du fichier tout en extrayant des éléments.

Un objet `basic_istream<Char_T, Tr>` de magasins de classe:

- Un objet de base [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>`publique virtuel de classe .

- Un nombre d’extraction pour la dernière `count` opération d’entrée non formée (appelée dans le code précédent).

## <a name="example"></a>Exemple

Consultez l’exemple de [basic_ifstream, classe](../standard-library/basic-ifstream-class.md) pour en savoir plus sur les flux d’entrée.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_istream](#basic_istream)|Construit un objet de type `basic_istream`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[gcount](#gcount)|Retourne le nombre de caractères lus au cours de la dernière entrée non mise en forme.|
|[get](#get)|Lit un ou plusieurs caractères dans le flux d'entrée.|
|[getline](#getline)|Lit une ligne dans le flux d'entrée.|
|[Ignorer](#ignore)|Ignore un certain nombre d'éléments à partir de la position de lecture actuelle.|
|[Peek](#peek)|Retourne le caractère suivant à lire.|
|[putback](#putback)|Place un caractère spécifié dans le flux.|
|[Lire](#read)|Lit un nombre spécifié de caractères dans le flux et les stocke dans un tableau.|
|[readsome](#readsome)|Lire seulement dans la mémoire tampon.|
|[seekg](#seekg)|Déplace la position de lecture dans un flux.|
|[sentry](#sentry)|La classe imbriquée décrit un objet dont la déclaration structure les fonctions d'entrée mise en forme et les fonctions d'entrée non mise en forme.|
|[swap](#swap)|Échange cet objet `basic_istream` pour le paramètre d'objet `basic_istream` fourni.|
|[Synchronisation](#sync)|Synchronise le dispositif d’entrée associé au flux avec le tampon du flux.|
|[tellg](#tellg)|Indique la position de lecture actuelle dans le flux.|
|[unget](#unget)|Replace le dernier caractère lu dans le flux.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[>>de l’opérateur](#op_gt_gt)|Appelle une fonction sur le flux d'entrée ou lit les données mises en forme dans le flux d'entrée.|
|[opérateur](#op_eq)|Affecte le `basic_istream` du côté droit de l'opérateur à cet objet. Il s’agit d’une affectation de déménagement impliquant une `rvalue` référence qui ne laisse pas une copie derrière.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<istream>

**Espace de noms :** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream::basic_istream

Construit un objet de type `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Paramètres

*strbuf (strbuf)*\
Objet de type [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**vrai** si c’est un flux standard; autrement, **faux**.

*Oui*\
Objet `basic_istream` à copier.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)`de base en appelant . Il stocke également zéro dans le nombre d’extractions. Pour plus d’informations sur ce nombre d’extraction, consultez la section Remarques de la [vue d’ensemble de](../standard-library/basic-istream-class.md) la classe basic_istream.

Le deuxième constructeur initialise la classe de base en appelant `move(right)`. Il stocke `right.gcount()` également dans le nombre d’extraction et stocke zéro dans le nombre d’extraction pour «droit».

### <a name="example"></a>Exemple

Consultez l’exemple de [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) pour en savoir plus sur les flux d’entrée.

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream::gcount

Retourne le nombre de caractères lus au cours de la dernière entrée non mise en forme.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’extractions.

### <a name="remarks"></a>Notes

Utilisez [basic_istream::get](#get) pour lire les caractères sans mise en forme.

### <a name="example"></a>Exemple

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream::get

Lit un ou plusieurs caractères dans le flux d'entrée.

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>Paramètres

*Compter*\
Nombre de caractères à lire à partir de *strbuf*.

*Délimiteur*\
Le personnage qui devrait mettre fin à la lecture si elle est rencontrée avant *le compte*.

*Str*\
Chaîne dans laquelle écrire.

*Ch*\
Caractère à obtenir.

*strbuf (strbuf)*\
Mémoire tampon dans laquelle écrire.

### <a name="return-value"></a>Valeur de retour

La forme sans paramètre de get retourne l’élément lu comme un entier ou la fin du fichier. Les autres formes retournent le flux (* `this`).

### <a name="remarks"></a>Notes

La première fonction d’entrée non formée extrait un élément, `rdbuf->sbumpc`si possible, comme si en retournant . Sinon, il `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)revient . Si la fonction n’extrait [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`aucun élément, elle appelle .

La deuxième fonction extrait l’élément [int_type](../standard-library/basic-ios-class.md#int_type)`meta` de la même manière. Si `meta` compare égale `traits_type::eof`à , `setstate(failbit)`la fonction appelle . Sinon, il `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` stocke à *Ch*. La fonction __renvoie à ce point__.

La troisième `get(str, count, widen('\n'))`fonction revient .

La quatrième fonction extrait `count - 1` jusqu’à des éléments et les stocke dans le tableau à partir *de str*. Elle stocke toujours `char_type` après les éléments extraits qu’elle stocke. Pour les besoins du test, l’extraction s’arrête :

- À la fin du fichier.

- Après la fonction extrait un élément qui se compare égal à *delimiter*. Dans ce cas, l’élément est remis à la séquence contrôlée.

- Après la fonction `count - 1` extrait des éléments.

Si la fonction n’extrait aucun élément, elle appelle `setstate(failbit)`. En tout cas, il revient __à ce sujet__.

La cinquième `get(strbuf, widen('\n'))`fonction revient .

La sixième fonction extrait des éléments et les insère dans *strbuf*. L’extraction s’arrête en fin de dossier ou sur un élément qui se compare à égal au *délimital*, qui n’est pas extrait. Elle s’arrête également, sans extraire l’élément en question, si une insertion échoue ou lève une exception (qui est interceptée, mais n’est pas levée à nouveau). Si la fonction n’extrait aucun élément, elle appelle `setstate(failbit)`. Dans tous les cas, la fonction __renvoie à ce point__.

### <a name="example"></a>Exemple

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream::getline

Obtient une ligne du flux d’entrée.

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>Paramètres

*Compter*\
Nombre de caractères à lire à partir de *strbuf*.

*Délimiteur*\
Le personnage qui devrait mettre fin à la lecture si elle est rencontrée avant *le compte*.

*Str*\
Chaîne dans laquelle écrire.

### <a name="return-value"></a>Valeur de retour

Le flux __(ceci__).

### <a name="remarks"></a>Notes

La première de ces fonctions d’entrée non formées revient `getline(str, count, widen('\n'))`.

La deuxième fonction extrait `count - 1` jusqu’à des éléments et les stocke dans le tableau à partir *de str*. Elle stocke toujours le caractère de fin de chaîne après tous les éléments extraits qu’elle stocke. Pour les besoins du test, l’extraction s’arrête :

- À la fin du fichier.

- Après la fonction extrait un élément qui se compare égal à *delimiter*. Dans ce cas, l’élément n’est pas remis, et il n’est pas annexé à la séquence contrôlée.

- Après la fonction `count - 1` extrait des éléments.

Si la fonction n’extrait aucun élément ou `count - 1` élément, elle appelle [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`. En tout cas, il revient __à ce sujet__.

### <a name="example"></a>Exemple

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream::ignorer

Ignore un certain nombre d'éléments à partir de la position de lecture actuelle.

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>Paramètres

*Compter*\
Nombre d’éléments à ignorer à partir de la position de lecture actuelle.

*Délimiteur*\
L’élément qui, s’il `ignore` est rencontré avant le compte, provoque le retour et permettant à tous les éléments après *délimititer* d’être lu.

### <a name="return-value"></a>Valeur de retour

Le flux __(ceci__).

### <a name="remarks"></a>Notes

La fonction d’entrée non formée extrait pour *compter* les éléments et les rejette. Si *le* `numeric_limits<int>::max`nombre est égal, cependant, il est considéré comme arbitrairement grand. L’extraction s’arrête tôt à `Ch` la `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` fin du fichier ou sur un élément tel qui se compare à égal à *delimiter* (qui est également extrait). La fonction __renvoie à ce point__.

### <a name="example"></a>Exemple

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>istream de base::opérateur\_>>

Appelle une fonction sur le flux d'entrée ou lit les données mises en forme dans le flux d'entrée.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>Paramètres

*Pfn Pfn*\
Pointeur de fonction.

*strbuf (strbuf)*\
Objet de type `stream_buf`.

*Val*\
Valeur à lire à partir du flux.

### <a name="return-value"></a>Valeur de retour

Le flux __(ceci__).

### <a name="remarks"></a>Notes

L’en-tête \<istream> définit également plusieurs opérateurs d’extraction mondiaux. Pour plus d’informations, consultez [operator>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt).

La fonction de premier membre assure `istr >> ws` qu’une expression du formulaire appelle, [`ws`](../standard-library/istream-functions.md#ws) `(istr)`puis renvoie __ce__. Les deuxième et troisième fonctions garantissent [`hex`](../standard-library/ios-functions.md#hex)que d’autres manipulateurs, tels que , se comportent de la même façon. Les fonctions restantes sont les fonctions d’entrée formatées.

La fonction :

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

extrait des éléments, si *strbuf* n’est pas un pointeur nul, et les insère dans *strbuf*. L’extraction s’arrête à la fin du fichier. Elle s’arrête également, sans extraire l’élément en question, si une insertion échoue ou lève une exception (qui est interceptée, mais n’est pas levée à nouveau). Si la fonction n’extrait [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`aucun élément, elle appelle . Dans tous les cas, la fonction __renvoie à ce point__.

La fonction :

```cpp
basic_istream& operator>>(bool& val);
```

extrait un champ et le convertit en [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `), Init(0), *this, getloc, val)`une valeur Boolean en appelant . Ici, `InIt` est [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>`défini comme . La fonction __renvoie à ce point__.

Chacune des fonctions :

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

extraire un champ et le convertir `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)`en valeur numérique en appelant . Ici, `InIt` est `istreambuf_iterator<Char_T, Tr>`défini comme , et *val* a le type **long**, **non signé long,** ou **vide** <strong>\*</strong> au besoin.

Si la valeur convertie ne peut pas être représentée comme [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`le type de *val*, la fonction appelle . Dans tous les cas, la fonction __renvoie à ce point__.

Chacune des fonctions :

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

extraire un champ et le convertir `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)`en valeur numérique en appelant . Ici, `InIt` est `istreambuf_iterator<Char_T, Tr>`défini comme , et *val* a le type **double** ou **long double** au besoin.

Si la valeur convertie ne peut pas *val*être représentée comme `setstate(failbit)`le type de val , la fonction appelle . En tout cas, il revient __à ce sujet__.

### <a name="example"></a>Exemple

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream::opérateur

Affecte le `basic_istream` du côté droit de l'opérateur à cet objet. Il s’agit d’une affectation de déménagement impliquant une `rvalue` référence qui ne laisse pas une copie derrière.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence `rvalue` à un objet `basic_ifstream`.

### <a name="return-value"></a>Valeur de retour

Retours __-ceci__.

### <a name="remarks"></a>Notes

L’opérateur `swap(right)`membre appelle .

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream::pek

Retourne le caractère suivant à lire.

```cpp
int_type peek();
```

### <a name="return-value"></a>Valeur de retour

Caractère suivant à lire.

### <a name="remarks"></a>Notes

La fonction d’entrée non formée extrait un élément, `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc)si possible, comme si en retournant . Sinon, il `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)revient .

### <a name="example"></a>Exemple

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream::putback

Place un caractère spécifié dans le flux.

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Paramètres

*Ch*\
Caractère à remettre dans le flux.

### <a name="return-value"></a>Valeur de retour

Le flux __(ceci__).

### <a name="remarks"></a>Notes

La [fonction d’entrée non formée](../standard-library/basic-istream-class.md) remet *Ch*, [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc)si possible, comme si en appelant . S’il `rdbuf` s’agit d’un `sputbackc` `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)pointeur nul, ou si l’appel à retourner , la fonction appelle [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)`. En tout cas, il revient __à ce sujet__.

### <a name="example"></a>Exemple

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream::lire

Lit un nombre spécifié de caractères dans le flux et les stocke dans un tableau.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes.

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*Str*\
Tableau dans lequel lire les caractères.

*Compter*\
Nombre de caractères à lire.

### <a name="return-value"></a>Valeur de retour

Le flux ( `*this`).

### <a name="remarks"></a>Notes

La fonction d’entrée non formée extrait pour *compter* les éléments et les stocke dans le tableau à partir *de str*. L’extraction s’arrête tôt à la [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`fin du fichier, auquel cas la fonction appelle . En tout cas, il revient __à ce sujet__.

### <a name="example"></a>Exemple

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream::readsome

Lit le nombre spécifié de valeurs de caractère.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*Str*\
Tableau dans lequel `readsome` stocke les caractères qu’il lit.

*Compter*\
Nombre de caractères à lire.

### <a name="return-value"></a>Valeur de retour

Le nombre de caractères effectivement lu, [`gcount`](#gcount).

### <a name="remarks"></a>Notes

Cette fonction d’entrée non formée extrait pour *compter* les éléments du flux d’entrée et les stocke dans la *str*de tableau.

Cette fonction n’attend pas d’entrée. Elle lit toutes les données disponibles.

### <a name="example"></a>Exemple

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream::seekg

Déplace la position de lecture dans un flux.

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Paramètres

*Pos*\
Position absolue à laquelle déplacer le pointeur de lecture.

*hors tension*\
Un décalage pour déplacer le pointeur de lecture par rapport à *la manière*.

*Façon*\
Une des énumérations [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

### <a name="return-value"></a>Valeur de retour

Le flux __(ceci__).

### <a name="remarks"></a>Notes

La première fonction membre effectue une recherche absolue, la deuxième fonction membre effectue une recherche relative.

> [!NOTE]
> N’utilisez pas la deuxième fonction membre avec des fichiers texte, car la norme C++ ne prend pas en charge les recherches relative dans des fichiers texte.

Si [`fail`](../standard-library/basic-ios-class.md#fail) elle est fausse, `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)`la fonction `pos_type` du `newpos`premier membre appelle , pour un objet temporaire . Si `fail` elle est fausse, `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)`la deuxième fonction appelle . Dans les deux `(off_type)newpos == (off_type)(-1)` cas, si (l’opération `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`de positionnement échoue), la fonction appelle . Les deux fonctions reviennent __à ce point.__

Si [`fail`](../standard-library/basic-ios-class.md#fail) c’est vrai, les fonctions des membres ne font rien.

### <a name="example"></a>Exemple

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream::sentry

La classe imbriquée décrit un objet dont la déclaration structure les fonctions d’entrée avec et sans mise en forme.

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>Notes

Si `_Istr.` [`good`](../standard-library/basic-ios-class.md#good) c’est vrai, le constructeur:

- `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) Appels `->` s’il `_Istr.tie` n’est pas un pointeur [`flush`](../standard-library/basic-ostream-class.md#flush) nul.

- [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` Appels efficaces si `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) est nonzero.

Si après une `_Istr.good` telle préparation, est `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`faux, le constructeur appelle . Dans tous les cas, le constructeur `_Istr.good` `status`stocke la valeur retournée par . Un appel `operator bool` ultérieur pour délivre cette valeur stockée.

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream::swap

Échange le contenu de deux objets `basic_istream`.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence lvalue à un objet `basic_istream`.

### <a name="remarks"></a>Notes

La fonction [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)`membre appelle . Il échange également le nombre d’extraction avec le nombre d’extraction pour *le droit*.

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream::sync

Synchronise le dispositif d’entrée associé au flux avec le tampon du flux.

```cpp
int sync();
```

### <a name="return-value"></a>Valeur de retour

S’il [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) s’agit d’un pointeur nul, la fonction renvoie -1. Sinon, il `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync)appelle . Si cet appel renvoie -1, la fonction appelle [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` et renvoie -1. Sinon, la fonction retourne zéro.

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream::tellg

Indique la position de lecture actuelle dans le flux.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Valeur de retour

Position actuelle dans le flux.

### <a name="remarks"></a>Notes

Si [`fail`](../standard-library/basic-ios-class.md#fail) elle est fausse, [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)`la fonction du membre revient . Sinon, `pos_type(-1)`est retourné.

### <a name="example"></a>Exemple

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream::unget

Replace le dernier caractère lu dans le flux.

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>Valeur de retour

Le flux __(ceci__).

### <a name="remarks"></a>Notes

La [fonction d’entrée non formée](../standard-library/basic-istream-class.md) remet l’élément précédent dans le `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc)flux, si possible, comme si en appelant . S’il [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) s’agit d’un `sungetc` `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof)pointeur nul, ou si l’appel à retourner , la fonction appelle [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)`. En tout cas, il revient __à ce sujet__.

Pour plus `unget` d’informations [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc)sur la façon d’échouer, voir .

### <a name="example"></a>Exemple

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>Voir aussi

[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
