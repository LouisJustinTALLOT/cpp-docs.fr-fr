---
description: 'En savoir plus sur : classe basic_ifstream'
title: basic_ifstream, classe
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
ms.openlocfilehash: 6968c6f1987a5261d06d53af24616281d84a0e3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321558"
---
# <a name="basic_ifstream-class"></a>basic_ifstream, classe

Décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`>, avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Elem*\
Élément de base de la mémoire tampon de fichier.

*TR*\
Caractéristiques de l’élément de base de la mémoire tampon de fichier (généralement `char_traits`< `Elem`>).

## <a name="remarks"></a>Notes

L’objet stocke un objet de classe `basic_filebuf`< `Elem`, `Tr`>.

## <a name="example"></a>Exemple

L'exemple suivant montre comment lire le texte d'un fichier.

```cpp
// basic_ifstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_class.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="input-basic_ifstream_classtxt"></a>Entrée : basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>Output

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_ifstream](#basic_ifstream)|Initialise une nouvelle instance d'un objet `basic_ifstream`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[close](#close)|Ferme un fichier.|
|[is_open](#is_open)|Détermine si un fichier est ouvert.|
|[open](#open)|Ouvre un fichier.|
|[rdbuf](#rdbuf)|Retourne l'adresse de la mémoire tampon de flux stockée.|
|[swap](#swap)|Échange le contenu de ce `basic_ifstream` avec le contenu du `basic_ifstream` fourni.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#op_eq)|Assigne le contenu de cet objet de flux. Il s'agit d'une assignation de déplacement impliquant une `rvalue` qui ne laisse pas de copie.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<fstream>

**Espace de noms :** std

## <a name="basic_ifstreambasic_ifstream"></a><a name="basic_ifstream"></a> basic_ifstream :: basic_ifstream

Construit un objet de type `basic_ifstream`.

```cpp
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```

### <a name="parameters"></a>Paramètres

*_Filename*\
Nom du fichier à ouvrir.

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Protection d’ouverture de fichier par défaut, équivalente au paramètre `shflag` dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant [basic_istream](../standard-library/basic-istream-class.md)( `sb` ), où `sb` est l’objet stocké de la classe [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`>. Il initialise également `sb` en appelant `basic_filebuf`< `Elem`, `Tr`>.

Les deuxième et troisième constructeurs initialisent la classe de base en appelant `basic_istream`( `sb`). Elle s’initialise également `sb` en appelant [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf) <  `Elem` , `Tr`>, puis `sb` . [ouvrez](../standard-library/basic-filebuf-class.md#open)( `_Filename` , `_Mode` &#124; `ios_base::in` ). Si la dernière fonction retourne un pointeur null, le constructeur appelle **SetState**( `failbit` ).

Le quatrième constructeur initialise l’objet avec le contenu de `right`, traité comme une référence rvalue.

### <a name="example"></a>Exemple

L'exemple suivant montre comment lire le texte d'un fichier. Pour créer le fichier, consultez l’exemple de [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

```cpp
// basic_ifstream_ctor.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_ctor.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="basic_ifstreamclose"></a><a name="close"></a> basic_ifstream :: Close

Ferme un fichier.

```cpp
void close();
```

### <a name="remarks"></a>Notes

La fonction membre appelle [rdbuf](#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `close`.

## <a name="basic_ifstreamis_open"></a><a name="is_open"></a> basic_ifstream :: is_open

Détermine si un fichier est ouvert.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le fichier est ouvert ; **`false`** sinon,.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Exemple

Consultez [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) pour obtenir un exemple qui utilise `is_open`.

## <a name="basic_ifstreamopen"></a><a name="open"></a> basic_ifstream :: Open

Ouvre un fichier.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
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
Protection d’ouverture de fichier par défaut, équivalente au paramètre `shflag` dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Notes

La fonction membre appelle [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` &#124; **ios_base :: in**). Si Open échoue, la fonction appelle [SetState](../standard-library/basic-ios-class.md#setstate)( `failbit` ), ce qui peut lever une exception ios_base :: Failure.

### <a name="example"></a>Exemple

Consultez [basic_filebuf :: Open](../standard-library/basic-filebuf-class.md#open) pour obtenir un exemple qui utilise `open` .

## <a name="basic_ifstreamoperator"></a><a name="op_eq"></a> basic_ifstream :: Operator =

Assigne le contenu de cet objet de flux. Il s'agit d'une assignation de déplacement qui implique une rvalue qui ne laisse pas de copie.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence rvalue à un objet `basic_ifstream`.

### <a name="return-value"></a>Valeur renvoyée

Retourne **`*this`** .

### <a name="remarks"></a>Notes

L’opérateur membre remplace le contenu de l’objet à l’aide du contenu de *droite*, traité comme une référence rvalue. Pour plus d’informations, consultez [Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="basic_ifstreamrdbuf"></a><a name="rdbuf"></a> basic_ifstream :: rdbuf

Retourne l'adresse de la mémoire tampon de flux stockée.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [basic_filebuf](../standard-library/basic-filebuf-class.md) qui représente la mémoire tampon de flux stockée.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="basic_ifstreamswap"></a><a name="swap"></a> basic_ifstream :: swap

Échange le contenu de deux objets `basic_ifstream`.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence à une autre mémoire tampon de flux.

### <a name="remarks"></a>Notes

La fonction membre échange le contenu de cet objet pour le contenu de *Right*.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
