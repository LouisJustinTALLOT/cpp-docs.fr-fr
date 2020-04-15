---
title: basic_fstream, classe
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
ms.openlocfilehash: 80992430d6bef6fc46106452dfaa44cc0ed9e71c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376861"
---
# <a name="basic_fstream-class"></a>basic_fstream, classe

Décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets codés à l’aide d’un tampon de `Tr`flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, avec des éléments de type `Elem`, dont les traits de caractère sont déterminés par la classe .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Elem*\
Élément de base de la mémoire tampon de fichier.

*Tr*\
Caractéristiques de l’élément de base de la mémoire tampon de fichier (généralement `char_traits`< `Elem`>).

## <a name="remarks"></a>Notes

L’objet stocke un objet de classe `basic_filebuf`< `Elem`, `Tr`>.

> [!NOTE]
> Les pointeurs get et put d’un objet fstream ne sont **PAS** indépendants l’un de l’autre. Si le pointeur get bouge, le pointeur put bouge aussi.

## <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet `basic_fstream` qui peut être lu et écrit.

```cpp
// basic_fstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);
    if (!fs.bad())
    {
        // Write to the file.
        fs << "Writing to a basic_fstream object..." << endl;
        fs.close();

        // Dump the contents of the file to cout.
        fs.open("fstream.txt", ios::in);
        cout << fs.rdbuf();
        fs.close();
    }
}
```

```Output
Writing to a basic_fstream object...
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_fstream](#basic_fstream)|Construit un objet de type `basic_fstream`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Proche](#close)|Ferme un fichier.|
|[is_open](#is_open)|Détermine si un fichier est ouvert.|
|[open](#open)|Ouvre un fichier.|
|[rdbuf](#rdbuf)|Retourne l’adresse du tampon de flux stocké, du `Tr` pointeur de type à< `Elem` [basic_filebuf,](../standard-library/basic-filebuf-class.md)>.|
|[swap](#swap)|Échange le contenu de cet objet avec le contenu d'un autre objet `basic_fstream`.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<fstream>

**Espace de noms :** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a>basic_fstream::basic_fstream

Construit un objet de type `basic_fstream`.

```cpp
basic_fstream();

explicit basic_fstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```

### <a name="parameters"></a>Paramètres

*_Filename*\
Nom du fichier à ouvrir.

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
La protection d’ouverture de fichier par défaut, équivalente au paramètre *shflag* dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base`sb`en `sb` appelant [basic_iostream](../standard-library/basic-iostream-class.md)( ), où est l’objet stocké de la classe [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>. Il est également `sb` parasémis `basic_filebuf` \< en appelant **Elem**, **Tr**>.

Les deuxième et troisième constructeurs initialisent la classe de base en appelant `basic_iostream`( **sb**). Il est également `sb` parasémis `basic_filebuf` \< en appelant **Elem**, **Tr**>, puis `_Mode` **sb.**[ouvert](../standard-library/basic-filebuf-class.md#open) *(Filename*, ). Si cette dernière fonction renvoie un pointeur`failbit`nul, le constructeur appelle [setstate](../standard-library/basic-ios-class.md#setstate)( ).

Le quatrième constructeur initialise l’objet avec le contenu de `right`, traité comme une référence rvalue.

### <a name="example"></a>Exemple

Consultez [streampos](../standard-library/ios-typedefs.md#streampos) pour obtenir un exemple qui utilise `basic_fstream`.

## <a name="basic_fstreamclose"></a><a name="close"></a>basic_fstream::fermer

Ferme un fichier.

```cpp
void close();
```

### <a name="remarks"></a>Notes

La fonction membre appelle [rdbuf](#rdbuf) **->** [fermer](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `close`.

## <a name="basic_fstreamis_open"></a><a name="is_open"></a>basic_fstream::is_open

Détermine si un fichier est ouvert.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le fichier est ouvert, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Exemple

Consultez [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) pour obtenir un exemple d’utilisation de `is_open`.

## <a name="basic_fstreamopen"></a><a name="open"></a>basic_fstream::ouvert

Ouvre un fichier.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Paramètres

*_Filename*\
Nom du fichier à ouvrir.

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
La protection d’ouverture de fichier par défaut, équivalente au paramètre *shflag* dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Notes

La fonction membre appelle [rdbuf](#rdbuf) **->** [ouvert](../standard-library/basic-filebuf-class.md#open) `_Mode` *(Filename*, ). Si cette fonction renvoie un pointeur `failbit`nul, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Exemple

Voir [basic_filebuf::ouvrir](../standard-library/basic-filebuf-class.md#open) pour un exemple de `open`la façon d’utiliser .

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a>basic_fstream::opérateur

Assigne à cet objet le contenu d'un objet de flux spécifié. Il s'agit d'une assignation de déplacement qui implique une rvalue qui ne laisse pas de copie.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence lvalue à un objet `basic_fstream`.

### <a name="return-value"></a>Valeur de retour

Retourne `*this`.

### <a name="remarks"></a>Notes

L’opérateur membre remplace le contenu de l’objet en utilisant le contenu du *droit,* traité comme une référence rvalue.

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a>basic_fstream::rdbuf

Retourne l’adresse de la mémoire tampon de flux stockée, de type pointeur à [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valeur de retour

Adresse de la mémoire tampon de flux stockée.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="basic_fstreamswap"></a><a name="swap"></a>basic_fstream::swap

Échange le contenu de deux objets `basic_fstream`.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence `lvalue` à un objet `basic_fstream`.

### <a name="remarks"></a>Notes

La fonction membre échange le contenu de cet objet et le contenu du *droit*.

## <a name="see-also"></a>Voir aussi

[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
