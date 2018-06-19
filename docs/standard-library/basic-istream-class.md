---
title: basic_istream, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22dc1282dc165941c1a611583138c2d9aed51090
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848922"
---
# <a name="basicistream-class"></a>basic_istream, classe

Décrit un objet qui contrôle l’extraction d’éléments et d’objets codés à partir d’une mémoire tampon de flux avec des éléments de type `Elem`, également appelé [char_type](../standard-library/basic-ios-class.md#char_type), dont les caractéristiques sont déterminées par la classe *Tr*, également appelée [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
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

Les deux groupes de fonctions appellent [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) s’ils rencontrent la fin du fichier lors de l’extraction d’éléments.

Un objet de la classe `basic_istream`< `Elem`, *Tr*> stocke :

- Un objet de base public virtuel de la classe [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, *Tr*> `.`

- Nombre d’extractions pour la dernière opération d’entrée non mise en forme (appelé **count** dans le code précédent).

## <a name="example"></a>Exemple

Consultez l’exemple de [basic_ifstream, classe](../standard-library/basic-ifstream-class.md) pour en savoir plus sur les flux d’entrée.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_istream](#basic_istream)|Construit un objet de type `basic_istream`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[gcount](#gcount)|Retourne le nombre de caractères lus au cours de la dernière entrée non mise en forme.|
|[get](#get)|Lit un ou plusieurs caractères dans le flux d'entrée.|
|[getline](#getline)|Lit une ligne dans le flux d'entrée.|
|[ignore](#ignore)|Ignore un certain nombre d'éléments à partir de la position de lecture actuelle.|
|[peek](#peek)|Retourne le caractère suivant à lire.|
|[putback](#putback)|Place un caractère spécifié dans le flux.|
|[read](#read)|Lit un nombre spécifié de caractères dans le flux et les stocke dans un tableau.|
|[readsome](#readsome)|Lire seulement dans la mémoire tampon.|
|[seekg](#seekg)|Déplace la position de lecture dans un flux.|
|[sentry](#sentry)|La classe imbriquée décrit un objet dont la déclaration structure les fonctions d'entrée mise en forme et les fonctions d'entrée non mise en forme.|
|[swap](#swap)|Échange cet objet `basic_istream` pour le paramètre d'objet `basic_istream` fourni.|
|[sync](#sync)|Synchronise le périphérique d’entrée associé au flux avec la mémoire tampon du flux.|
|[tellg](#tellg)|Indique la position de lecture actuelle dans le flux.|
|[unget](#unget)|Replace le dernier caractère lu dans le flux.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator>>](#op_gt_gt)|Appelle une fonction sur le flux d'entrée ou lit les données mises en forme dans le flux d'entrée.|
|[operator=](#op_eq)|Affecte le `basic_istream` du côté droit de l'opérateur à cet objet. Il s'agit d'une assignation de déplacement qui implique une référence `rvalue` qui ne laisse pas de copie.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<istream>

**Espace de noms :** std

## <a name="basic_istream"></a>  basic_istream::basic_istream

Construit un objet de type `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Paramètres

`strbuf` Un objet de type [basic_streambuf](../standard-library/basic-streambuf-class.md).

`_Isstd` `true` s’il s’agit d’un flux standard ; dans le cas contraire, `false`.

`right` A `basic_istream` objet à copier.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant [init](../standard-library/basic-ios-class.md#init)(_S`trbuf`). Il stocke également zéro dans le nombre d’extractions. Pour plus d’informations sur ce nombre d’extractions, consultez la section Notes de la rubrique de présentation [basic_istream, classe](../standard-library/basic-istream-class.md).

Le deuxième constructeur initialise la classe de base en appelant `move( right)`. Il stocke également _R `ight.gcount()` dans le nombre d’extractions et stocke zéro dans le nombre d’extractions pour _R `ight`.

### <a name="example"></a>Exemple

Consultez l’exemple de [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) pour en savoir plus sur les flux d’entrée.

## <a name="gcount"></a>  basic_istream::gcount

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

```Output

a

```

```Output

      aType the letter 'a':
a
1
```

## <a name="get"></a>  basic_istream::get

Lit un ou plusieurs caractères dans le flux d'entrée.

```cpp
int_type get();

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```

### <a name="parameters"></a>Paramètres

`count` Le nombre de caractères à lire à partir de `strbuf`.

`Delim` Le caractère qui doit s’arrêter la lecture, si elle se trouve avant `count`.

`str` Une chaîne dans laquelle écrire.

`Ch` Un caractère à obtenir.

`strbuf` Une mémoire tampon dans lequel écrire.

### <a name="return-value"></a>Valeur de retour

La forme sans paramètre de get retourne l’élément lu comme un entier ou la fin du fichier. Les autres formes retournent le flux (* `this`).

### <a name="remarks"></a>Notes

La première de ces fonctions d’entrée sans mise en forme extrait un élément, si possible, en retournant `rdbuf`-> `sbumpc`. Sinon, elle retourne **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). Si la fonction n’extrait aucun élément, elle appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).

La deuxième fonction extrait l’élément [int_type](../standard-library/basic-ios-class.md#int_type) `meta` de la même manière. Si la valeur de `meta` est égale à **traits_type::eof**, la fonction appelle `setstate`( **failbit**). Sinon, elle stocke **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)( `meta`) dans `Ch`. La fonction retourne **\*this**.

La troisième fonction retourne **get**(_ *Str*, `count`, `widen`(’\ **n**’)).

La quatrième fonction extrait jusqu’à `count` - 1 éléments et les stocke dans le tableau en commençant par _ *Str*. Elle stocke toujours `char_type` après les éléments extraits qu’elle stocke. Pour les besoins du test, l’extraction s’arrête :

- À la fin du fichier.

- Une fois que la fonction a extrait un élément dont la valeur est égale à `Delim`. Dans ce cas, l’élément est remis dans la séquence contrôlée.

- Une fois que la fonction a extrait `count` - 1 éléments.

Si la fonction n’extrait aucun élément, elle appelle `setstate`( **failbit**). Dans tous les cas, elle retourne **\*this**.

La cinquième fonction retourne **get**( **strbuf**, `widen`(’\ **n**’)).

La sixième fonction extrait des éléments et les insère dans **strbuf**. L’extraction s’arrête à la fin du fichier ou sur un élément dont la valeur est égale à _ *Delim,* qui n’est pas extrait. Elle s’arrête également, sans extraire l’élément en question, si une insertion échoue ou lève une exception (qui est interceptée, mais n’est pas levée à nouveau). Si la fonction n’extrait aucun élément, elle appelle `setstate`( **failbit**). Dans tous les cas, la fonction retourne **\*this**.

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

## <a name="getline"></a>  basic_istream::getline

Obtient une ligne du flux d’entrée.

```cpp
basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type Delim);
```

### <a name="parameters"></a>Paramètres

`count` Le nombre de caractères à lire à partir de **strbuf**.

`Delim` Le caractère qui doit s’arrêter la lecture, si elle se trouve avant `count`.

`str` Une chaîne dans laquelle écrire.

### <a name="return-value"></a>Valeur de retour

Le flux ( **\*this**).

### <a name="remarks"></a>Notes

La première de ces fonctions d’entrée sans mise en forme retourne **getline**(_ *Str*, `count`, `widen`(’ `\`**n**’)).

La deuxième fonction extrait jusqu’à `count` - 1 éléments et les stocke dans le tableau en commençant par _ *Str*. Elle stocke toujours le caractère de fin de chaîne après tous les éléments extraits qu’elle stocke. Pour les besoins du test, l’extraction s’arrête :

- À la fin du fichier.

- Une fois que la fonction a extrait un élément dont la valeur est égale à `Delim`. Dans ce cas, l’élément n’est ni remis à sa place, ni ajouté à la séquence contrôlée.

- Une fois que la fonction a extrait `count` - 1 éléments.

Si la fonction n’extrait aucun élément ou extrait `count` - 1 éléments, elle appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Dans tous les cas, elle retourne **\*this**.

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

## <a name="ignore"></a>  basic_istream::ignore

Ignore un certain nombre d'éléments à partir de la position de lecture actuelle.

```cpp
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Paramètres

`count` Le nombre d’éléments à ignorer de la position de lecture actuelle.

`Delim` L’élément qui, si rencontrée avant count, déclenche **ignorer** à retourner et permettre à tous les éléments après `Delim` à lire.

### <a name="return-value"></a>Valeur de retour

Le flux ( **\*this**).

### <a name="remarks"></a>Notes

La fonction d’entrée sans mise en forme extrait jusqu’à `count` éléments et les ignore. Si `count` est égal à **numeric_limits\<int>:: max**, toutefois, il est considéré comme arbitrairement grand. L’extraction s’arrête au début de la fin du fichier ou sur un élément `Ch` telles que **traits_type ::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) compare égal à *Delim* (qui sont également extraites). La fonction retourne **\*this**.

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

## <a name="op_gt_gt"></a>  basic\_istream::operator>>

Appelle une fonction sur le flux d'entrée ou lit les données mises en forme dans le flux d'entrée.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));
basic_istream& operator>>(basic_streambuf<Elem, Tr>* strbuf);
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

`Pfn` Un pointeur de fonction.

`strbuf` Un objet de type **stream_buf**.

`val` Valeur à lire à partir du flux.

### <a name="return-value"></a>Valeur de retour

Le flux ( **\*this**).

### <a name="remarks"></a>Notes

Le \<istream > en-tête définit également plusieurs opérateurs d’extraction global. Pour plus d’informations, consultez [operator>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt).

La première fonction membre garantit qu’une expression de la forme **istr** >> `ws` appelle [ws](../standard-library/istream-functions.md#ws)( **istr**), puis retourne **\*this**. Les deuxième et troisième fonctions garantissent que d’autres manipulateurs, comme [hex](../standard-library/ios-functions.md#hex), se comportent de la même façon. Les fonctions restantes constituent les fonctions d’entrée mises en forme.

La fonction :

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

extrait des éléments, si _ *Strbuf* n’est pas un pointeur null, et les insère dans `strbuf`. L’extraction s’arrête à la fin du fichier. Elle s’arrête également, sans extraire l’élément en question, si une insertion échoue ou lève une exception (qui est interceptée, mais n’est pas levée à nouveau). Si la fonction n’extrait aucun élément, elle appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Dans tous les cas, la fonction retourne **\*this**.

La fonction :

```cpp
basic_istream& operator>>(bool& val);
```

extrait un champ et le convertit en valeur booléenne en appelant [use_facet](../standard-library/basic-filebuf-class.md#open) < `num_get`\< **Elem**, **InIt**>( [getloc](../standard-library/ios-base-class.md#getloc)). [get](../standard-library/ios-base-class.md#getloc)( **InIt**( [rdbuf](../standard-library/basic-ios-class.md#rdbuf)), `Init`(0), **\*this**, `getloc`, `val`). Ici, **InIt** est défini comme [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)\< **Elem**, **Tr**>. La fonction retourne **\*this**.

Les fonctions :

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

extraient chacune un champ et le convertissent en valeur numérique en appelant `use_facet`< `num_get`\< **Elem**, **InIt**>( `getloc`). [get](#get)( **InIt**( `rdbuf`), `Init`(0), **\*this**, `getloc`, `val`). Ici, **InIt** est défini en tant que `istreambuf_iterator` \< **Elem**, **Tr**>, et `val` a un type **long**,`unsigned long`, ou **void \***  en fonction des besoins.

Si la valeur convertie ne peut pas être représentée comme le type de `val`, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Dans tous les cas, la fonction retourne **\*this**.

Les fonctions :

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

extraient chacune un champ et le convertissent en valeur numérique en appelant `use_facet`< `num_get`\< **Elem**, **InIt**>( `getloc`). **get**( **InIt**( `rdbuf`), `Init`(0), **\*this**, `getloc`, `val`). Ici, **InIt** est défini comme `istreambuf_iterator`\< **Elem**, **Tr**> et `val` a le type **double** ou `long double` selon les besoins.

Si la valeur convertie ne peut pas être représentée comme le type de `val`, la fonction appelle `setstate`( **failbit**). Dans tous les cas, elle retourne **\*this**.

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

## <a name="op_eq"></a>  basic_istream::operator=

Affecte le `basic_istream` du côté droit de l'opérateur à cet objet. Il s'agit d'une assignation de déplacement qui implique une référence `rvalue` qui ne laisse pas de copie.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Paramètres

`right` Un `rvalue` font référence à un `basic_ifstream` objet.

### <a name="return-value"></a>Valeur de retour

Retourne *this.

### <a name="remarks"></a>Notes

L’opérateur membre appelle swap `( right)`.

## <a name="peek"></a>  basic_istream::peek

Retourne le caractère suivant à lire.

```cpp
int_type peek();
```

### <a name="return-value"></a>Valeur de retour

Caractère suivant à lire.

### <a name="remarks"></a>Notes

La fonction d’entrée sans mise en forme extrait un élément, si possible, en retournant `rdbuf` -> [sgetc](../standard-library/basic-streambuf-class.md#sgetc). Sinon, elle retourne **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

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

```Output

abcde

```

```Output

      abcdeType 'abcde': abcde
a abcde
```

## <a name="putback"></a>  basic_istream::putback

Place un caractère spécifié dans le flux.

```cpp
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Paramètres

`Ch` Un caractère remettre dans le flux de données.

### <a name="return-value"></a>Valeur de retour

Le flux ( **\*this**).

### <a name="remarks"></a>Notes

La [fonction d’entrée sans mise en forme](../standard-library/basic-istream-class.md) remet `Ch`, si possible, en appelant [rdbuf](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc](../standard-library/basic-streambuf-class.md#sputbackc). Si rdbuf est un pointeur null ou si l’appel à `sputbackc` retourne **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **badbit**). Dans tous les cas, elle retourne **\*this**.

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

## <a name="read"></a>  basic_istream::read

Lit un nombre spécifié de caractères dans le flux et les stocke dans un tableau.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes.

```cpp
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

`str` Tableau dans lequel lire les caractères.

`count` Le nombre de caractères à lire.

### <a name="return-value"></a>Valeur de retour

Le flux ( `*this`).

### <a name="remarks"></a>Notes

La deuxième fonction d’entrée sans mise en forme extrait jusqu’à `count` éléments et les stocke dans le tableau en commençant par _ `Str`. L’extraction s’arrête dès le début de la fin du fichier, auquel cas la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit`). Dans tous les cas, elle retourne `*this`.

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

```Output

abcde

```

```Output

      abcdeType 'abcde': abcde
abcde
```

## <a name="readsome"></a>  basic_istream::readsome

Lit le nombre spécifié de valeurs de caractère.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

`str` Le tableau dans lequel `readsome` stocke les caractères lus.

`count` Le nombre de caractères à lire.

### <a name="return-value"></a>Valeur de retour

Nombre de caractères véritablement lus, [gcount](#gcount).

### <a name="remarks"></a>Notes

Cette fonction d’entrée sans mise en forme extrait jusqu’à `count` éléments du flux d’entrée et les stocke dans le tableau `str`.

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

## <a name="seekg"></a>  basic_istream::seekg

Déplace la position de lecture dans un flux.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Paramètres

`pos` La position absolue dans lequel vous souhaitez déplacer le pointeur de la lecture.

`off` Déplacez le pointeur de lecture relatif à un offset `way`.

`way` Parmi les [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) énumérations.

### <a name="return-value"></a>Valeur de retour

Le flux ( **\*this**).

### <a name="remarks"></a>Notes

La première fonction membre effectue une recherche absolue, la deuxième fonction membre effectue une recherche relative.

> [!NOTE]
> N’utilisez pas la deuxième fonction membre avec des fichiers texte, car la norme C++ ne prend pas en charge les recherches relative dans des fichiers texte.

Si [fail](../standard-library/basic-ios-class.md#fail) a la valeur false, la première fonction membre appelle **newpos** = [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`), pour certains objets temporaires **pos_type** **newpos**. Si **fail** a la valeur false, la deuxième fonction appelle **newpos** = **rdbuf** -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`). Dans les deux cas, si ( `off_type`) **newpos** == ( `off_type`)(-1) (l’opération de positionnement échoue), la fonction appelle **istr**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Les deux fonctions retournent **\*this**.

Si [fail](../standard-library/basic-ios-class.md#fail) a la valeur true, les fonctions membres n’effectuent aucune action.

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

## <a name="sentry"></a>  basic_istream::sentry

La classe imbriquée décrit un objet dont la déclaration structure les fonctions d’entrée avec et sans mise en forme.

sentry de classe {public : sentry explicite (basic_istream\<Elem, Tr > & _Istr, bool _Noskip = false) ; bool() opérateur const ;} ;

### <a name="remarks"></a>Notes

Si `_Istr.`[good](../standard-library/basic-ios-class.md#good) a la valeur true, le constructeur :

- Appelle `_Istr`. [tie](../standard-library/basic-ios-class.md#tie) -> [flush](../standard-library/basic-ostream-class.md#flush) si `_Istr`. `tie` n’est pas un pointeur null

- Appelle [ws](../standard-library/istream-functions.md#ws)( `_Istr`) si `_Istr`. [flags](../standard-library/ios-base-class.md#flags)**&**[skipws](../standard-library/ios-functions.md#skipws) est différent de zéro

Si, après toute cette préparation, `_Istr`. **good** a la valeur false, le constructeur appelle `_Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Dans tous les cas, le constructeur stocke la valeur retournée par `_Istr`. **good** dans **status**. Un appel ultérieur à **operator bool** fournit cette valeur stockée.

## <a name="swap"></a>  basic_istream::swap

Échange le contenu de deux objets `basic_istream`.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Paramètres

`right` Référence lvalue à un `basic_istream` objet.

### <a name="remarks"></a>Notes

La fonction membre appelle [basic_ios::swap](../standard-library/basic-ios-class.md#swap)`(right)`. Elle échange également le nombre d'extractions avec le nombre d'extractions pour `right`.

## <a name="sync"></a>  basic_istream::sync

Synchronise le périphérique d’entrée associé au flux avec la mémoire tampon du flux.

```cpp
int sync();
```

### <a name="return-value"></a>Valeur de retour

Si [rdbuf](../standard-library/basic-ios-class.md#rdbuf) est un pointeur null, la fonction retourne -1. Sinon, elle appelle `rdbuf` ->  [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Si le résultat est -1, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **badbit**) et retourne -1. Sinon, la fonction retourne zéro.

## <a name="tellg"></a>  basic_istream::tellg

Indique la position de lecture actuelle dans le flux.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Valeur de retour

Position actuelle dans le flux.

### <a name="remarks"></a>Notes

Si [fail](../standard-library/basic-ios-class.md#fail) a la valeur false, la fonction membre retourne [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**). Sinon, elle retourne `pos_type`(-1).

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

## <a name="unget"></a>  basic_istream::unget

Replace le dernier caractère lu dans le flux.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Valeur de retour

Le flux ( **\*this**).

### <a name="remarks"></a>Notes

La [fonction d’entrée sans mise en forme](../standard-library/basic-istream-class.md) remet l’élément précédent dans le flux, si possible, en appelant `rdbuf` -> [sungetc](../standard-library/basic-streambuf-class.md#sungetc). Si [rdbuf](../standard-library/basic-ios-class.md#rdbuf) est un pointeur null ou si l’appel à `sungetc` retourne **traits_type::**[eof](../standard-library/basic-ios-class.md#eof), la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **badbit**). Dans tous les cas, elle retourne **\*this**.

Pour plus d’informations sur l’échec possible de `unget`, consultez [basic_streambuf::sungetc](../standard-library/basic-streambuf-class.md#sungetc).

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

```Output

abc

```

```Output

      abcType 'abc': abc
abc
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
