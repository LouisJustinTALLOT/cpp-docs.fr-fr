---
description: 'En savoir plus sur : classe basic_streambuf'
title: basic_streambuf, classe
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
ms.openlocfilehash: 7600c60c501c1922deeabca11d41c89bc37548a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325611"
---
# <a name="basic_streambuf-class"></a>basic_streambuf, classe

Décrit une classe de base abstraite pour dériver une mémoire tampon de flux qui contrôle la transmission des éléments depuis et vers une représentation spécifique d'un flux.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Paramètres

*Elem*\
Un [char_type](#char_type).

*TR*\
Le [traits_type](#traits_type) du caractère.

## <a name="remarks"></a>Notes

Le modèle de classe décrit une classe de base abstraite pour dériver une mémoire tampon de flux qui contrôle la transmission d’éléments vers et à partir d’une représentation spécifique d’un flux. Un objet de classe `basic_streambuf` permet de contrôler un flux avec des éléments de type *TR*, également appelés [char_type](#char_type), dont les caractéristiques sont déterminées par la classe [char_traits](../standard-library/char-traits-struct.md), également appelée [traits_type](#traits_type).

Chaque mémoire tampon de flux contrôle conceptuellement deux flux indépendants : un pour les extractions (entrée) et un pour les insertions (sortie). Une représentation spécifique peut cependant rendre l'un ou l'autre (ou les deux) de ces flux inaccessible. Elle conserve en général une relation entre les deux flux. Ce que vous insérez dans le flux de sortie d’un [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` , `Tr`> objet, par exemple, est ce que vous extrayez ultérieurement de son flux d’entrée. Lorsque vous positionnez un flux d’un [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`> objet, vous positionnez l’autre flux en tandem.

L’interface publique du modèle de classe `basic_streambuf` fournit les opérations qui sont communes à tous les tampons de flux, mais spécialisées. L'interface protégée fournit les opérations nécessaires pour qu'une représentation spécifique d'un flux effectue son travail. Les fonctions membres virtuelles protégées vous permettent de personnaliser le comportement d'une mémoire tampon de flux dérivée pour une représentation spécifique d'un flux. Chaque mémoire tampon de flux dérivée de cette bibliothèque décrit comment elle spécialise le comportement de ses fonctions membres virtuelles protégées. Le comportement par défaut pour la classe de base, qui est souvent de ne rien faire, est décrit dans cette rubrique.

Les fonctions membres protégées restantes contrôlent la copie de et vers le stockage fourni pour mettre en mémoire tampon les transmissions vers et depuis des flux. Par exemple, une mémoire tampon d'entrée est caractérisée par :

- [eback](#eback), un pointeur vers le début de la mémoire tampon.

- [gptr](#gptr), un pointeur vers l’élément suivant à lire.

- [egptr](#egptr), un pointeur juste après la fin de la mémoire tampon.

De façon similaire, une mémoire tampon de sortie est caractérisée par :

- [pbase](#pbase), un pointeur vers le début de la mémoire tampon.

- [pptr](#pptr), un pointeur vers l’élément suivant à écrire.

- [epptr](#epptr), un pointeur juste après la fin de la mémoire tampon.

Pour toutes les mémoires tampons, le protocole suivant est utilisé :

- Si le pointeur suivant est null, c'est qu'il n'existe pas de mémoire tampon. Dans le cas contraire, les trois pointeurs pointent tous dans la même séquence. Ils peuvent être comparés de façon fiable quant à l'ordre.

- Pour une mémoire tampon de sortie, si le pointeur suivant est inférieur au pointeur de fin, vous pouvez stocker un élément à la position d'écriture désignée par le pointeur suivant.

- Pour une mémoire tampon d'entrée, si le pointeur suivant est inférieur au pointeur de fin, vous pouvez lire un élément à la position de lecture désignée par le pointeur suivant.

- Pour une mémoire tampon d'entrée, si le pointeur de début est inférieur au pointeur suivant, vous pouvez replacer un élément à la position de replacement désignée par le pointeur suivant décrémenté.

Les fonctions membres virtuelles protégées que vous écrivez pour une classe dérivée de `basic_streambuf`< `Elem`, `Tr`> doivent collaborer à la gestion de ce protocole.

Un objet de la classe `basic_streambuf`< `Elem`, `Tr`> stocke les six pointeurs décrits précédemment. Il stocke également un objet de paramètres régionaux dans un objet de type [locale](../standard-library/locale-class.md) pour une éventuelle utilisation par une mémoire tampon de flux dérivée.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_streambuf](#basic_streambuf)|Construit un objet de type `basic_streambuf`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Associe un nom de type au paramètre de modèle `Elem`.|
|[int_type](#int_type)|Associe un nom de type dans la portée `basic_streambuf` avec le paramètre de modèle `Elem`.|
|[off_type](#off_type)|Associe un nom de type dans la portée `basic_streambuf` avec le paramètre de modèle `Elem`.|
|[pos_type](#pos_type)|Associe un nom de type dans la portée `basic_streambuf` avec le paramètre de modèle `Elem`.|
|[traits_type](#traits_type)|Associe un nom de type au paramètre de modèle `Tr`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[eback](#eback)|Une fonction protégée qui retourne un pointeur vers le début de la mémoire tampon d'entrée.|
|[egptr](#egptr)|Une fonction protégée qui retourne un pointeur qui pointe juste après la fin de la mémoire tampon d'entrée.|
|[epptr](#epptr)|Une fonction protégée qui retourne un pointeur qui pointe juste après la fin de la mémoire tampon de sortie.|
|[gbump](#gbump)|Une fonction protégée qui ajoute `count` au pointeur suivant pour la mémoire tampon d'entrée.|
|[getloc](#getloc)|Obtient les paramètres régionaux de l'objet `basic_streambuf`.|
|[gptr](#gptr)|Une fonction protégée qui retourne un pointeur vers l'élément suivant de la mémoire tampon d'entrée.|
|[imbue](#imbue)|Fonction virtuelle protégée appelée par [pubimbue](#pubimbue).|
|[in_avail](#in_avail)|Retourne le nombre d'éléments qui sont prêts à être lus dans la mémoire tampon.|
|[surcharge](#overflow)|Fonction virtuelle protégée qui peut être appelée quand un nouveau caractère est inséré dans une mémoire tampon saturée.|
|[pbackfail](#pbackfail)|Une fonction membre virtuelle protégée qui tente de replacer un élément dans le flux d'entrée, puis d'en faire l'élément actif (pointé par le pointeur suivant).|
|[pbase](#pbase)|Une fonction protégée qui retourne un pointeur vers le début de la mémoire tampon de sortie.|
|[pbump](#pbump)|Une fonction protégée qui ajoute `count` au pointeur suivant pour la mémoire tampon de sortie.|
|[pptr](#pptr)|Une fonction protégée qui retourne un pointeur vers l'élément suivant de la mémoire tampon de sortie.|
|[pubimbue](#pubimbue)|Définit les paramètres régionaux de l'objet `basic_streambuf`.|
|[pubseekoff](#pubseekoff)|Appelle [seekoff](#seekoff), une fonction virtuelle protégée qui est remplacée dans une classe dérivée.|
|[pubseekpos](#pubseekpos)|Appelle [seekpos](#seekpos), une fonction virtuelle protégée qui est remplacée dans une classe dérivée et réinitialise la position actuelle du pointeur.|
|[pubsetbuf](#pubsetbuf)|Appelle [setbuf](#setbuf), une fonction virtuelle protégée qui est remplacée dans une classe dérivée.|
|[pubsync](#pubsync)|Appelle [sync](#sync), une fonction virtuelle protégée qui est remplacée dans une classe dérivée et met à jour le flux externe associé à cette mémoire tampon.|
|[sbumpc](#sbumpc)|Lit et retourne l'élément actuel, en déplaçant le pointeur du flux.|
|[seekoff](#seekoff)|La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.|
|[seekpos](#seekpos)|La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.|
|[setbuf](#setbuf)|La fonction membre virtuelle protégée effectue une opération spécifique à chaque mémoire tampon de flux dérivée.|
|[setg](#setg)|Une fonction protégée qui stocke `_Gbeg` dans le pointeur de début, `_Gnext` dans le pointeur suivant et `_Gend` dans le pointeur de fin pour la mémoire tampon d'entrée.|
|[setp](#setp)|Une fonction protégée qui stocke `_Pbeg` dans le pointeur de début et `_Pend` dans le pointeur suivant dans le pointeur de fin pour la mémoire tampon de sortie.|
|[sgetc](#sgetc)|Retourne l'élément actuel sans changer la position dans le flux.|
|[sgetn](#sgetn)|Retourne le nombre d'éléments lus.|
|[showmanyc](#showmanyc)|Fonction membre virtuelle protégée qui retourne le nombre de caractères qui peuvent être extraits du flux d'entrée et garantit que le programme ne sera pas soumis à un délai d'attente indéfini.|
|[snextc](#snextc)|Lit l'élément actuel et retourne l'élément suivant.|
|[sputbackc](#sputbackc)|Place un `char_type` dans le flux.|
|[sputc](#sputc)|Place un caractère dans le flux.|
|[sputn](#sputn)|Place une chaîne de caractères dans le flux.|
|[stossc](#stossc)|Se déplace après l'élément actuel du flux.|
|[sungetc](#sungetc)|Obtient un caractère du flux.|
|[swap](#swap)|Échange les valeurs de cet objet avec les valeurs du paramètre de l'objet `basic_streambuf`.|
|[synchronisation](#sync)|Une fonction virtuelle protégée qui tente de synchroniser les flux contrôlés avec tous les flux externes associés.|
|[uflow](#uflow)|Une fonction virtuelle protégée qui extrait l'élément actuel du flux d'entrée.|
|[underflow](#underflow)|Une fonction virtuelle protégée qui extrait l'élément actuel du flux d'entrée.|
|[xsgetn](#xsgetn)|Une fonction virtuelle protégée qui extrait des éléments du flux d'entrée.|
|[xsputn](#xsputn)|Une fonction virtuelle protégée qui insère des éléments dans le flux d'entrée.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#op_eq)|Assigne les valeurs de cet objet à partir d'un autre objet `basic_streambuf`.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<streambuf>

**Espace de noms :** std

## <a name="basic_streambufbasic_streambuf"></a><a name="basic_streambuf"></a> basic_streambuf :: basic_streambuf

Construit un objet de type `basic_streambuf`.

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence lvalue à l’objet `basic_streambuf` qui est utilisée pour définir les valeurs de cet objet `basic_streambuf`.

### <a name="remarks"></a>Notes

Le premier constructeur protégé stocke un pointeur null dans tous les pointeurs contrôlant la mémoire tampon d’entrée et la mémoire tampon de sortie. Il stocke également `locale::classic` dans l’objet de paramètres régionaux. Pour plus d’informations, consultez [locale::classic](../standard-library/locale-class.md#classic).

Le deuxième constructeur protégé copie les pointeurs et les paramètres régionaux à partir de la *droite*.

## <a name="basic_streambufchar_type"></a><a name="char_type"></a> basic_streambuf :: char_type

Associe un nom de type au paramètre de modèle **Elem**.

```cpp
typedef Elem char_type;
```

## <a name="basic_streambufeback"></a><a name="eback"></a> basic_streambuf :: eback

Une fonction protégée qui retourne un pointeur vers le début de la mémoire tampon d'entrée.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le début de la mémoire tampon d’entrée.

## <a name="basic_streambufegptr"></a><a name="egptr"></a> basic_streambuf :: egptr

Une fonction protégée qui retourne un pointeur qui pointe juste après la fin de la mémoire tampon d'entrée.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur juste après la fin de la mémoire tampon d’entrée.

## <a name="basic_streambufepptr"></a><a name="epptr"></a> basic_streambuf :: epptr

Une fonction protégée qui retourne un pointeur qui pointe juste après la fin de la mémoire tampon de sortie.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur juste après la fin de la mémoire tampon de sortie.

## <a name="basic_streambufgbump"></a><a name="gbump"></a> basic_streambuf :: gbump

Fonction protégée qui ajoute le *nombre* au pointeur suivant pour la mémoire tampon d’entrée.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Paramètres

*saut*\
Quantité de laquelle faire avancer le pointeur.

## <a name="basic_streambufgetloc"></a><a name="getloc"></a> basic_streambuf :: getloc

Obtient les paramètres régionaux de l’objet basic_streambuf.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Valeur renvoyée

Objet de paramètres régionaux stocké.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ios_base::getloc](../standard-library/ios-base-class.md#getloc).

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_getloc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="basic_streambufgptr"></a><a name="gptr"></a> basic_streambuf :: GPTR

Une fonction protégée qui retourne un pointeur vers l'élément suivant de la mémoire tampon d'entrée.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément suivant de la mémoire tampon d’entrée.

## <a name="basic_streambufimbue"></a><a name="imbue"></a> basic_streambuf :: imbue

Fonction virtuelle protégée appelée par [pubimbue](#pubimbue).

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Paramètres

*_Loc*\
Référence à des paramètres régionaux.

### <a name="remarks"></a>Notes

Le comportement par défaut consiste à n’effectuer aucune opération.

## <a name="basic_streambufin_avail"></a><a name="in_avail"></a> basic_streambuf :: in_avail

Retourne le nombre d'éléments qui sont prêts à être lus dans la mémoire tampon.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments prêts à être lus dans la mémoire tampon.

### <a name="remarks"></a>Notes

Si une [position de lecture](../standard-library/basic-streambuf-class.md) est disponible, la fonction membre retourne [egptr](#egptr)  -  [GPTR](#gptr). Sinon, elle retourne [showmanyc](#showmanyc).

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_in_avail.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   char c;
   // cin's buffer is empty, in_avail will return 0
   cout << cin.rdbuf( )->in_avail( ) << endl;
   cin >> c;
   cout << cin.rdbuf( )->in_avail( ) << endl;
}
```

## <a name="basic_streambufint_type"></a><a name="int_type"></a> basic_streambuf :: int_type

Associe un nom de type de la portée basic_streambuf à l’un des types d’un paramètre de modèle.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_streambufoff_type"></a><a name="off_type"></a> basic_streambuf :: off_type

Associe un nom de type de la portée basic_streambuf à l’un des types d’un paramètre de modèle.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_streambufoperator"></a><a name="op_eq"></a> basic_streambuf :: Operator =

Assigne les valeurs de cet objet à partir d'un autre objet `basic_streambuf`.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence lvalue à l'objet `basic_streambuf` qui est utilisée pour affecter des valeurs à cet objet.

### <a name="remarks"></a>Notes

L’opérateur membre protégé copie à partir de la *droite* les pointeurs qui contrôlent la mémoire tampon d’entrée et la mémoire tampon de sortie. Il stocke également `right.`[getloc()](#getloc) dans le `locale object`. Elle retourne **`*this`** .

## <a name="basic_streambufoverflow"></a><a name="overflow"></a> basic_streambuf :: overflow

Fonction virtuelle protégée qui peut être appelée quand un nouveau caractère est inséré dans une mémoire tampon saturée.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Paramètres

*_Meta*\
Caractère à insérer dans la mémoire tampon ou **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Valeur renvoyée

Si la fonction ne peut pas réussir, elle retourne **traits_type::eof** ou lève une exception. Sinon, elle retourne **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*). Le comportement par défaut consiste à retourner **traits_type::eof**.

### <a name="remarks"></a>Notes

Si *\_ meta* n’est pas égal à **traits_type :: EOF**, la fonction membre virtuelle protégée s’efforce d’insérer l’élément **traits_type ::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_ meta*) dans le flux de sortie. Elle peut le faire de différentes manières :

- Si une `write position` est disponible, elle peut stocker l’élément dans la position d’écriture et incrémenter le pointeur suivant pour la mémoire tampon de sortie.

- Elle peut rendre disponible une position d’écriture en allouant du stockage nouveau ou supplémentaire à la mémoire tampon de sortie.

- Elle peut rendre disponible une position d’écriture en écrivant, dans une destination externe quelconque, tout ou partie des éléments entre le pointeur de début et le suivant pour la mémoire tampon de sortie.

La fonction overflow virtuelle, avec les fonctions [sync](#sync) et [underflow](#underflow), définit les caractéristiques de la classe dérivée de streambuf. Chaque classe dérivée peut implémenter la fonction overflow de différentes façons, mais l’interface avec la classe de flux d’appel est la même.

La fonction `overflow` est souvent appelée par les fonctions publiques `streambuf` comme `sputc` et `sputn` quand la zone de placement est saturée, mais les autres classes, y compris les classes de flux, peuvent appeler `overflow` à tout moment.

La fonction consomme les caractères de la zone de placement entre les pointeurs `pbase` et `pptr`, puis réinitialise la zone de placement. La fonction `overflow` doit également consommer `nCh` (si `nCh` n’est pas `EOF`) ou elle peut choisir de placer ce caractère dans la nouvelle zone de placement pour qu’il soit utilisé lors du prochain appel.

La définition du mot consommation varie selon les classes dérivées. Par exemple, la classe `filebuf` écrit ses caractères dans un fichier, tandis que la classe `strstreambuf` les conserve dans sa mémoire tampon et (si la mémoire tampon est désignée comme étant dynamique) étend la mémoire tampon en réponse à un appel à la fonction overflow. Cette extension est obtenue en libérant l’ancienne mémoire tampon et en la remplaçant par une nouvelle mémoire tampon plus grande. Les pointeurs sont ajustés selon les besoins.

## <a name="basic_streambufpbackfail"></a><a name="pbackfail"></a> basic_streambuf : échec de la :p

Une fonction membre virtuelle protégée qui tente de replacer un élément dans le flux d'entrée, puis d'en faire l'élément actif (pointé par le pointeur suivant).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Paramètres

*_Meta*\
Caractère à insérer dans la mémoire tampon ou **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Valeur renvoyée

Si la fonction ne peut pas réussir, elle retourne **traits_type::eof** ou lève une exception. Sinon, elle retourne une autre valeur. Le comportement par défaut consiste à retourner **traits_type::eof**.

### <a name="remarks"></a>Notes

Si les *\_ métadonnées de métadonnées* sont égales à **traits_type :: EOF**, l’élément à envoyer à nouveau est effectivement celui qui se trouve déjà dans le flux avant l’élément actuel. Sinon, cet élément est remplacé par **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*). La fonction peut replacer un élément de différentes manières :

- Si une position où remettre l’élément est disponible, elle peut stocker l’élément dans cette position et décrémenter le pointeur suivant pour la mémoire tampon d’entrée.

- Elle peut rendre disponible une position en allouant du stockage nouveau ou supplémentaire à la mémoire tampon d’entrée.

- Pour une mémoire tampon de flux avec des flux d’entrée et de sortie courants, elle peut rendre disponible une position en écrivant, dans une destination externe quelconque, tout ou partie des éléments entre le pointeur de début et le suivant pour la mémoire tampon de sortie.

## <a name="basic_streambufpbase"></a><a name="pbase"></a> basic_streambuf : base :p

Une fonction protégée qui retourne un pointeur vers le début de la mémoire tampon de sortie.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le début de la mémoire tampon de sortie.

## <a name="basic_streambufpbump"></a><a name="pbump"></a> basic_streambuf ::p Bosselage

Fonction protégée qui ajoute *Count* au pointeur suivant pour la mémoire tampon de sortie.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre de caractères duquel avancer la position d’écriture.

## <a name="basic_streambufpos_type"></a><a name="pos_type"></a> basic_streambuf ::p os_type

Associe un nom de type de la portée basic_streambuf à l’un des types d’un paramètre de modèle.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_streambufpptr"></a><a name="pptr"></a> basic_streambuf : PTR :p

Une fonction protégée qui retourne un pointeur vers l'élément suivant de la mémoire tampon de sortie.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément suivant de la mémoire tampon de sortie.

## <a name="basic_streambufpubimbue"></a><a name="pubimbue"></a> basic_streambuf ::p ubimbue

Définit les paramètres régionaux de l’objet basic_streambuf.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>Paramètres

*_Loc*\
Référence à des paramètres régionaux.

### <a name="return-value"></a>Valeur renvoyée

Valeur précédente stockée dans l’objet de paramètres régionaux.

### <a name="remarks"></a>Notes

La fonction membre stocke _ *Loc* dans l’objet de paramètres régionaux et appelle [imbue](#imbue).

### <a name="example"></a>Exemple

Consultez [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) pour obtenir un exemple d’utilisation de `pubimbue`.

## <a name="basic_streambufpubseekoff"></a><a name="pubseekoff"></a> basic_streambuf ::p ubseekoff

Appelle [seekoff](#seekoff), une fonction virtuelle protégée qui est remplacée dans une classe dérivée.

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Off*\
Position à rechercher relative à *_Way*.

*_Way*\
Point de départ des opérations de décalage. Consultez [seekdir](../standard-library/ios-base-class.md#seekdir) pour connaître les valeurs possibles.

*_Which*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur renvoyée

Retourne la nouvelle position ou une position de flux non valide ( [seekoff](#seekoff)(_ *off*, `_Way` , `_Which` )).

### <a name="remarks"></a>Notes

Déplace le pointeur par rapport à *_Way*.

## <a name="basic_streambufpubseekpos"></a><a name="pubseekpos"></a> basic_streambuf ::p ubseekpos

Appelle [seekpos](#seekpos), une fonction virtuelle protégée qui est substituée dans une classe dérivée et réinitialise la position actuelle du pointeur.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Sp*\
Position à rechercher.

*_Which*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur renvoyée

Nouvelle position ou position de flux non valide. Pour déterminer si la position du flux n’est pas valide, comparez la valeur de retour à `pos_type(off_type(-1))`.

### <a name="remarks"></a>Notes

La fonction membre retourne [seekpos](#seekpos)(_ *Sp*, `_Which`).

## <a name="basic_streambufpubsetbuf"></a><a name="pubsetbuf"></a> basic_streambuf ::p ubsetbuf

Appelle [setbuf](#setbuf), une fonction virtuelle protégée qui est remplacée dans une classe dérivée.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*_Buffer*\
Pointeur vers `char_type` pour cette instanciation.

*saut*\
Taille de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Retourne [setbuf](#setbuf)( `_Buffer` , `count` ).

## <a name="basic_streambufpubsync"></a><a name="pubsync"></a> basic_streambuf ::p ubsync

Appelle [Sync](#sync), une fonction virtuelle protégée qui est substituée dans une classe dérivée et met à jour le flux externe associé à cette mémoire tampon.

```cpp
int pubsync();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la [synchronisation](#sync) ou-1 en cas d’échec.

## <a name="basic_streambufsbumpc"></a><a name="sbumpc"></a> basic_streambuf :: sbumpc

Lit et retourne l'élément actuel, en déplaçant le pointeur du flux.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Valeur renvoyée

Élément actuel.

### <a name="remarks"></a>Notes

Si une position de lecture est disponible, la fonction membre retourne **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong>[gptr](#gptr)) et incrémente le pointeur suivant pour la mémoire tampon d’entrée. Sinon, elle retourne [uflow](#uflow).

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_sbumpc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->sbumpc( );
   cout << i << endl;
}
```

```Input
3
```

```Output
33
51
```

## <a name="basic_streambufseekoff"></a><a name="seekoff"></a> basic_streambuf :: seekoff

Fonction membre virtuelle protégée qui tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Off*\
Position à rechercher relative à *_Way*.

*_Way*\
Point de départ des opérations de décalage. Consultez [seekdir](../standard-library/ios-base-class.md#seekdir) pour connaître les valeurs possibles.

*_Which*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur renvoyée

Retourne la nouvelle position ou une position de flux non valide ( `seekoff` (_ *off*, `_Way` , `_Which` )).

### <a name="remarks"></a>Notes

La nouvelle position est déterminée comme suit :

- Si `_Way` == `ios_base::beg`, la nouvelle position est le début du flux plus _ *Off*.

- Si `_Way` == `ios_base::cur`, la nouvelle position est la position actuelle du flux plus _ *Off*.

- Si `_Way` == `ios_base::end`, la nouvelle position est la fin du flux plus _ *Off*.

En règle générale, si **which & ios_base::in** est différent de zéro, le flux d’entrée est affecté et si **which & ios_base::out** est différent de zéro, le flux de sortie est affecté. Toutefois, l’utilisation réelle de ce paramètre varie selon les mémoires tampons de flux dérivées.

Si la fonction réussit à modifier la ou les positions du flux, elle retourne la ou les positions du flux qui en résultent. Sinon, elle retourne une position de flux non valide. Le comportement par défaut consiste à retourner une position de flux non valide.

## <a name="basic_streambufseekpos"></a><a name="seekpos"></a> basic_streambuf :: seekpos

Fonction membre virtuelle protégée qui tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Sp*\
Position à rechercher.

*_Which*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur renvoyée

Nouvelle position ou position de flux non valide. Pour déterminer si la position du flux n’est pas valide, comparez la valeur de retour à `pos_type(off_type(-1))`.

### <a name="remarks"></a>Notes

La nouvelle position est _ *Sp*.

En règle générale, si **which & ios_base::in** est différent de zéro, le flux d’entrée est affecté et si **which & ios_base::out** est différent de zéro, le flux de sortie est affecté. Toutefois, l’utilisation réelle de ce paramètre varie selon les mémoires tampons de flux dérivées.

Si la fonction réussit à modifier la ou les positions du flux, elle retourne la ou les positions du flux qui en résultent. Sinon, elle retourne une position de flux non valide (-1). Le comportement par défaut consiste à retourner une position de flux non valide.

## <a name="basic_streambufsetbuf"></a><a name="setbuf"></a> basic_streambuf :: setbuf

Fonction membre virtuelle protégée qui effectue une opération spécifique pour chaque mémoire tampon de flux dérivée.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*_Buffer*\
Pointeur vers une mémoire tampon.

*saut*\
Taille de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Le comportement par défaut consiste à retourner **`this`** .

### <a name="remarks"></a>Notes

Consultez [basic_filebuf](../standard-library/basic-filebuf-class.md). `setbuf` fournit une zone de mémoire pour l’objet `streambuf` à utiliser. La façon dont la mémoire tampon est utilisée est définie dans les classes dérivées.

## <a name="basic_streambufsetg"></a><a name="setg"></a> basic_streambuf :: SETG

Fonction protégée qui stocke _ *Gbeg* dans le pointeur de début, `_Gnext` dans le pointeur suivant et `_Gend` dans le pointeur de fin pour la mémoire tampon d’entrée.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Paramètres

*_Gbeg*\
Pointeur vers le début de la mémoire tampon.

*_Gnext*\
Pointeur vers un emplacement situé au milieu de la mémoire tampon.

*_Gend*\
Pointeur vers la fin de la mémoire tampon.

## <a name="basic_streambufsetp"></a><a name="setp"></a> basic_streambuf :: setp

Fonction protégée qui stocke *_Pbeg* dans le pointeur de début et *_Pend* dans le pointeur de fin pour la mémoire tampon de sortie.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Paramètres

*_Pbeg*\
Pointeur vers le début de la mémoire tampon.

*_Pend*\
Pointeur vers la fin de la mémoire tampon.

## <a name="basic_streambufsgetc"></a><a name="sgetc"></a> basic_streambuf :: sgetc

Retourne l'élément actuel sans changer la position dans le flux.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Valeur renvoyée

Élément actuel.

### <a name="remarks"></a>Notes

Si une position de lecture est disponible, la fonction membre retourne **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr)). Sinon, elle retourne [underflow](#underflow).

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_sgetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );

   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
   i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="basic_streambufsgetn"></a><a name="sgetn"></a> basic_streambuf :: sgetn

Extrait jusqu’à *Count* caractères de la mémoire tampon d’entrée et les stocke dans le *pointeur* de mémoire tampon fourni.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Mémoire tampon qui contient les caractères extraits.

*saut*\
Nombre d’éléments à lire.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments lus. Pour plus d’informations, consultez [streamsize](../standard-library/ios-typedefs.md#streamsize).

### <a name="remarks"></a>Notes

La fonction membre retourne [xsgetn](#xsgetn)( `ptr` , `count` ).

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_sgetn.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);
    char a[10];

    // Extract 3 characters from myfile and store them in a.
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996
    a[i] = myfile.widen('\0');

    // Display the size and contents of the buffer passed to sgetn.
    cout << i << " " << a << endl;

    // Display the contents of the original input buffer.
    cout << myfile.rdbuf() << endl;
}
```

## <a name="basic_streambufshowmanyc"></a><a name="showmanyc"></a> basic_streambuf :: showmanyc

Fonction membre virtuelle protégée qui retourne le nombre de caractères qui peuvent être extraits du flux d’entrée et garantit que le programme ne sera pas soumis à un délai d’attente indéfini.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Valeur renvoyée

Le comportement par défaut consiste à retourner zéro.

## <a name="basic_streambufsnextc"></a><a name="snextc"></a> basic_streambuf :: snextc

Lit l'élément actuel et retourne l'élément suivant.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Valeur renvoyée

Élément suivant dans le flux.

### <a name="remarks"></a>Notes

La fonction membre appelle [sbumpc](#sbumpc) et, si cette fonction retourne **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), retourne **traits_type::eof**. Sinon, elle retourne [sgetc](#sgetc).

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_snextc.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->snextc( );
   // cout << ( int )char_traits<char>::eof << endl;
   cout << i << endl;
}
```

```Input
aa
```

```Output
aa97
```

## <a name="basic_streambufsputbackc"></a><a name="sputbackc"></a> basic_streambuf :: sputbackc

Place un char_type dans le flux.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Paramètres

*_Ch*\
Le caractère.

### <a name="return-value"></a>Valeur renvoyée

Retourne le caractère ou un échec.

### <a name="remarks"></a>Notes

Si une position remise est disponible et que *_Ch* compare égal au caractère stocké dans cette position, la fonction membre décrémente le pointeur suivant pour la mémoire tampon d’entrée et retourne **traits_type ::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch` ). Sinon, elle retourne [pbackfail](#pbackfail)( `_Ch` ).

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_sputbackc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;

    ifstream myfile("basic_streambuf_sputbackc.txt",
        ios::in);

    int i = myfile.rdbuf()->sbumpc();
    cout << (char)i << endl;
    int j = myfile.rdbuf()->sputbackc('z');
    if (j == 'z')
    {
        cout << "it worked" << endl;
    }
    i = myfile.rdbuf()->sgetc();
    cout << (char)i << endl;
}
```

## <a name="basic_streambufsputc"></a><a name="sputc"></a> basic_streambuf :: sputc

Place un caractère dans le flux.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Paramètres

*_Ch*\
Le caractère.

### <a name="return-value"></a>Valeur renvoyée

Retourne le caractère, en cas de réussite.

### <a name="remarks"></a>Notes

Si un `write position` est disponible, la fonction membre stocke *_Ch* dans la position d’écriture, incrémente le pointeur suivant pour la mémoire tampon de sortie et retourne **traits_type ::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch` ). Dans le cas contraire, elle retourne [Overflow](#overflow)( `_Ch` ).

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_sputc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   int i = cout.rdbuf( )->sputc( 'a' );
   cout << endl << ( char )i << endl;
}
```

```Output
a
a
```

## <a name="basic_streambufsputn"></a><a name="sputn"></a> basic_streambuf :: sputn

Place une chaîne de caractères dans le flux.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Paramètres

*effectués*\
La chaîne de caractères.

*saut*\
Le nombre de caractères.

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères réellement insérés dans le flux.

### <a name="remarks"></a>Notes

La fonction membre retourne [xsputn](#xsputn)( `ptr` , `count` ). Consultez la section Notes de cette fonction membre pour plus d’informations.

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_sputn.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    streamsize i = cout.rdbuf()->sputn("test", 4);
    cout << endl << i << endl;
}
```

```Output
test
4
```

## <a name="basic_streambufstossc"></a><a name="stossc"></a> basic_streambuf :: stossc

Se déplace après l'élément actuel du flux.

```cpp
void stossc();
```

### <a name="remarks"></a>Notes

La fonction membre appelle [sbumpc](#sbumpc). Notez qu’une implémentation n’est pas nécessaire pour fournir cette fonction membre.

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_stossc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );

   myfile.rdbuf( )->stossc( );
   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="basic_streambufsungetc"></a><a name="sungetc"></a> basic_streambuf :: sungetc

Obtient un caractère du flux.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le caractère ou un échec.

### <a name="remarks"></a>Notes

Si une position remise est disponible, la fonction membre décrémente le pointeur suivant pour la mémoire tampon d’entrée et retourne `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [GPTR](#gptr)). Toutefois, il n’est pas toujours possible de déterminer le dernier caractère lu pour qu’il soit capturé dans l’état de la mémoire tampon actuelle. Si la valeur est true, la fonction retourne [pbackfail](#pbackfail). Pour éviter cette situation, suivez le caractère à remettre et appelez `sputbackc(ch)`, qui n’échoue pas, sauf si vous l’appelez au début du flux et que vous essayez de remettre plusieurs caractères.

### <a name="example"></a>Exemple

```cpp
// basic_streambuf_sungetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );

   // Read and increment
   int i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Read and increment
   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Decrement, read, and do not increment
   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;
}
```

## <a name="basic_streambufswap"></a><a name="swap"></a> basic_streambuf :: swap

Échange les valeurs de cet objet avec celles de l'objet `basic_streambuf` fourni.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence lvalue à l'objet `basic_streambuf`  utilisée pour échanger des valeurs.

### <a name="remarks"></a>Notes

La fonction membre protégée échange avec à *droite* tous les pointeurs contrôlant le `input buffer` et le `output buffer` . Elle échange également `right.`[getloc()](#getloc) avec l’objet `locale`.

## <a name="basic_streambufsync"></a><a name="sync"></a> basic_streambuf :: Sync

Une fonction virtuelle protégée qui tente de synchroniser les flux contrôlés avec tous les flux externes associés.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Valeur renvoyée

Si la fonction ne peut pas réussir, elle retourne -1. Le comportement par défaut consiste à retourner zéro.

### <a name="remarks"></a>Notes

`sync` implique l’écriture de tous les éléments entre le pointeur de début et le suivant pour la mémoire tampon de sortie. Elle n’implique pas de remettre les éléments entre les pointeurs suivants et le pointeur de fin pour la mémoire tampon d’entrée.

## <a name="basic_streambuftraits_type"></a><a name="traits_type"></a> basic_streambuf :: traits_type

Associe un nom de type au paramètre de modèle **Tr**.

```cpp
typedef Tr traits_type;
```

## <a name="basic_streambufuflow"></a><a name="uflow"></a> basic_streambuf :: uflow

Une fonction virtuelle protégée qui extrait l'élément actuel du flux d'entrée.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Valeur renvoyée

Élément actuel.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée essaie d’extraire l’élément actuel **ch** du flux d’entrée, puis avance la position du flux actuel et retourne l’élément sous la forme **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Elle peut le faire de différentes manières :

- Si une position de lecture est disponible, elle accepte **ch** comme élément stocké dans la position de lecture et avance le pointeur suivant pour la mémoire tampon d’entrée.

- Elle peut lire un élément directement à partir d’une source externe et le remettre avec la valeur **ch**.

- Pour une mémoire tampon de flux avec des flux d’entrée et de sortie communs, elle peut rendre disponible une position de lecture en écrivant dans une destination externe quelconque tout ou partie des éléments entre le pointeur de début et le suivant pour la mémoire tampon de sortie. Sinon, elle peut allouer du stockage nouveau ou supplémentaire à la mémoire tampon d’entrée. La fonction lit ensuite un ou plusieurs éléments à partir d’une source externe.

Si la fonction ne peut pas être exécutée correctement, elle retourne **traits_type ::**[EOF](../standard-library/char-traits-struct.md#eof)ou lève une exception. Sinon, elle retourne l’élément actuel `ch` dans le flux d’entrée, converti comme décrit ci-dessus, et avance le pointeur suivant pour la mémoire tampon d’entrée. Le comportement par défaut consiste à appeler [underflow](#underflow) et, si cette fonction retourne **traits_type::eof**,à retourner **traits_type::eof**. Sinon, la fonction retourne l’élément actuel **ch** dans le flux d’entrée, converti comme décrit précédemment, et avance le pointeur suivant pour la mémoire tampon d’entrée.

## <a name="basic_streambufunderflow"></a><a name="underflow"></a> basic_streambuf :: dépassement de capacité négatif

Fonction virtuelle protégée pour extraire l'élément actif du flux d'entrée.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Valeur renvoyée

Élément actuel.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée s’efforce d’extraire l’élément actuel **ch** du flux d’entrée, sans avancer la position du flux actuel, et le retourne comme `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Elle peut le faire de différentes manières :

- Si une position de lecture est disponible, **ch** est l’élément stocké dans la position de lecture. Pour plus d’informations, consultez la section Notes de [basic_streambuf, classe](../standard-library/basic-streambuf-class.md).

- Elle peut rendre disponible une position de lecture en allouant du stockage nouveau ou supplémentaire à la mémoire tampon d’entrée, puis en lisant un ou plusieurs éléments à partir d’une source externe. Pour plus d’informations, consultez la section Notes de [basic_streambuf, classe](../standard-library/basic-streambuf-class.md).

Si la fonction ne peut pas être exécutée correctement, elle retourne `traits_type::` [EOF](../standard-library/char-traits-struct.md#eof) `()` ou lève une exception. Sinon, elle retourne l’élément actuel dans le flux d’entrée, converti comme décrit précédemment. Le comportement par défaut consiste à retourner `traits_type::eof()`.

La fonction `underflow` virtuelle, avec les fonctions [sync](#sync) et [underflow](#overflow), définit les caractéristiques de la classe dérivée de `streambuf`. Chaque classe dérivée peut implémenter `underflow` de différentes façons, mais l’interface avec la classe de flux d’appel est la même.

La fonction `underflow` est souvent appelée par les fonctions publiques `streambuf` comme [sgetc](#sgetc) et [sgetn](#sgetn) quand la zone de récupération est vide, mais les autres classes, y compris les classes de flux, peuvent appeler `underflow` à tout moment.

La fonction `underflow` fournit des caractères à la zone de récupération à partir de la source d’entrée. Si la zone de récupération contient des caractères, `underflow` retourne le premier caractère. Si la zone de récupération est vide, la fonction remplit la zone et retourne le caractère suivant (qu’elle laisse dans la zone de récupération). Si plus aucun caractère n’est disponible, `underflow` retourne `EOF` et laisse vide la zone de récupération.

Dans la classe `strstreambuf`, `underflow` ajuste le pointeur [egptr](#egptr) pour accéder au stockage alloué dynamiquement par un appel à `overflow`.

## <a name="basic_streambufxsgetn"></a><a name="xsgetn"></a> basic_streambuf :: xsgetn

Fonction virtuelle protégée qui extrait les éléments du flux d’entrée.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Mémoire tampon qui contient les caractères extraits.

*saut*\
Nombre d’éléments à extraire.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments extraits.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée extrait jusqu’à *Count* éléments du flux d’entrée, comme en cas d’appels répétés à [sbumpc](#sbumpc), et les stocke dans le tableau en commençant par *ptr*. Elle retourne le nombre d’éléments réellement extraits.

## <a name="basic_streambufxsputn"></a><a name="xsputn"></a> basic_streambuf :: xsputn

Fonction virtuelle protégée qui insère les éléments dans le flux de sortie.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Pointeur vers les éléments à insérer.

*saut*\
Nombre d’éléments à insérer.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments réellement insérés dans le flux.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée insère jusqu’à *Count* éléments dans le flux de sortie, comme en cas d’appels répétés à [sputc](#sputc), à partir du tableau en commençant par *ptr*. L’insertion de caractères dans le flux de sortie s’arrête une fois que tous les caractères de *nombre* ont été écrits, ou si l’appel de `sputc( count)` retourne `traits::eof()` . Elle retourne le nombre d’éléments réellement insérés.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
