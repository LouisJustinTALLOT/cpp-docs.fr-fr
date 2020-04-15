---
title: basic_ofstream, classe
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
ms.openlocfilehash: f2d0facd92e0ef1935f8218a6d323a62edb81e5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376796"
---
# <a name="basic_ofstream-class"></a>basic_ofstream, classe

Décrit un objet qui contrôle l’insertion d’éléments et d’objets codés dans un tampon de `Elem`flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, avec des éléments de type , dont les traits de caractère sont déterminés par la classe `Tr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Elem*\
Élément de base de la mémoire tampon de fichier.

*Tr*\
Caractéristiques de l’élément de base de la mémoire tampon de fichier (généralement `char_traits`< `Elem`>).

## <a name="remarks"></a>Notes

Lorsque la **wchar_t** spécialisation `basic_ofstream` des écrits au fichier, si le fichier est ouvert en mode texte, il écrira une séquence MBCS. La représentation interne utilisera une mémoire tampon de caractères `wchar_t`.

L’objet stocke un objet de classe `basic_filebuf`< `Elem`, `Tr`>.

## <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet `basic_ofstream` et y écrire du texte.

```cpp
// basic_ofstream_class.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_ofstream](#basic_ofstream)|Crée un objet de type `basic_ofstream`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Proche](#close)|Ferme un fichier.|
|[is_open](#is_open)|Détermine si un fichier est ouvert.|
|[open](#open)|Ouvre un fichier.|
|[rdbuf](#rdbuf)|Retourne l'adresse de la mémoire tampon de flux stockée.|
|[swap](#swap)|Échange le contenu de ce `basic_ofstream` avec le contenu du `basic_ofstream` fourni.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur](#op_eq)|Assigne le contenu de cet objet de flux. Il s'agit d'une assignation de déplacement impliquant une `rvalue reference` qui ne laisse pas de copie.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<fstream>

**Espace de noms :** std

## <a name="basic_ofstreambasic_ofstream"></a><a name="basic_ofstream"></a>basic_ofstream::basic_ofstream

Crée un objet de type `basic_ofstream`.

```cpp
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```

### <a name="parameters"></a>Paramètres

*_Filename*\
Nom du fichier à ouvrir.

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Protection d’ouverture de fichier par défaut, équivalente au paramètre `shflag` dans [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

*Oui*\
Référence rvalue à l’objet `basic_ofstream` utilisé pour initialiser cet objet `basic_ofstream`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base`sb`en `sb` appelant [basic_ostream](../standard-library/basic-ostream-class.md)( ), où `Tr` est l’objet stocké de la classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>. Il initialise également `sb` en appelant `basic_filebuf`< `Elem`, `Tr`>.

Les deuxième et troisième constructeurs initialisent la classe de base en appelant `basic_ostream`( **sb**). Il est également `sb` para `basic_filebuf` <  `Elem` `Tr` initialisé en appelant `sb`,>, puis . [ouvert](../standard-library/basic-filebuf-class.md#open) `_Filename`( `_Mode` , &#124; `ios_base::out`). Si cette dernière fonction renvoie un pointeur`failbit`nul, le constructeur appelle [setstate](../standard-library/basic-ios-class.md#setstate)( ).

Le quatrième constructeur est une fonction de copie. Il initialise l’objet avec le contenu du *droit,* traité comme une référence rvalue.

### <a name="example"></a>Exemple

L'exemple suivant montre comment créer un objet `basic_ofstream` et y écrire du texte.

```cpp
// basic_ofstream_ctor.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("C:\\ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

## <a name="basic_ofstreamclose"></a><a name="close"></a>basic_ofstream::fermer

Ferme un fichier.

```cpp
void close();
```

### <a name="remarks"></a>Notes

La fonction membre appelle [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[fermer](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `close`.

## <a name="basic_ofstreamis_open"></a><a name="is_open"></a>basic_ofstream::is_open

Indique si un fichier est ouvert.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si le fichier est ouvert, **false** dans le cas contraire.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Exemple

```cpp
// basic_ofstream_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   // Open and close with a basic_filebuf
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );
   file.close( );
   if (file.is_open())
      cout << "it's open" << endl;
   else
      cout << "it's closed" << endl;
}
```

## <a name="basic_ofstreamopen"></a><a name="open"></a>basic_ofstream::ouvert

Ouvre un fichier.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
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

La fonction membre appelle [rdbuf](#rdbuf) **->** [ouvert](../standard-library/basic-filebuf-class.md#open) `_Mode` *(Filename*, &#124; ). `ios_base::out` Si cette fonction renvoie un pointeur`failbit`nul, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Exemple

Voir [basic_filebuf::ouvrir](../standard-library/basic-filebuf-class.md#open) pour un exemple `open`qui utilise .

## <a name="basic_ofstreamoperator"></a><a name="op_eq"></a>basic_ofstream::opérateur

Assigne le contenu de cet objet de flux. Il s'agit d'une assignation de déplacement impliquant une `rvalue reference` qui ne laisse pas de copie.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence rvalue à un objet `basic_ofstream`.

### <a name="return-value"></a>Valeur de retour

Retourne `*this`.

### <a name="remarks"></a>Notes

L’opérateur membre remplace le contenu de l’objet en utilisant le contenu du *droit,* traité comme une référence rvalue.

## <a name="basic_ofstreamrdbuf"></a><a name="rdbuf"></a>basic_ofstream::rdbuf

Retourne l'adresse de la mémoire tampon de flux stockée.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valeur de retour

Retourne l'adresse de la mémoire tampon de flux stockée.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="basic_ofstreamswap"></a><a name="swap"></a>basic_ofstream::swap

Échange le contenu de deux objets `basic_ofstream`.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence `lvalue` à un autre objet `basic_ofstream`.

### <a name="remarks"></a>Notes

La fonction membre échange le contenu de cet objet pour le contenu du *droit*.

## <a name="see-also"></a>Voir aussi

[Classe basic_ostream](../standard-library/basic-ostream-class.md)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
