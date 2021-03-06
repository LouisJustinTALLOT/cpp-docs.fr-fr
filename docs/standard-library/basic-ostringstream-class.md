---
description: 'En savoir plus sur : classe basic_ostringstream'
title: basic_ostringstream, classe
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: b745f6b733d093b620e15d0aa22593713988caf9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325639"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream, classe

Décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **elem**, **TR**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Utilis*\
Classe allocator.

*Elem*\
Type de l'élément de base de la chaîne.

*TR*\
Caractéristique spécialisée sur l'élément de base de la chaîne.

## <a name="remarks"></a>Notes

La classe décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux, avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` , et dont les éléments sont alloués par un allocateur de classe `Alloc` . L’objet stocke un objet de classe basic_stringbuf<**Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Construit un objet de type `basic_ostringstream`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Le type est un synonyme du paramètre de modèle *Alloc*.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[rdbuf](#rdbuf)|Retourne l’adresse de la mémoire tampon de flux stockée de type `pointer` à [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` , `Tr` , `Alloc`>.|
|[str](#str)|Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<sstream>

**Espace de noms :** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a> basic_ostringstream :: allocator_type

Le type est un synonyme du paramètre de modèle *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a> basic_ostringstream :: basic_ostringstream

Construit un objet de type basic_ostringstream.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objet de type `basic_string`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant [basic_ostream](../standard-library/basic-ostream-class.md)( **SB**), où `sb` est l’objet stocké de la classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **elem**, **TR**, `Alloc`>. Il initialise également **sb** en appelant basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`).

Le deuxième constructeur initialise la classe de base en appelant basic_ostream( **sb**). Elle s’initialise également `sb` en appelant basic_stringbuf< **elem**, **TR**, `Alloc`> (_ *Str*, `_Mode` &#124; `ios_base::out` ).

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a> basic_ostringstream :: rdbuf

Retourne l’adresse de la mémoire tampon de flux stockée de type `pointer` à [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **elem**, **TR**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valeur renvoyée

Adresse de la mémoire tampon de flux stockée, de type `pointer` à basic_stringbuf< **elem**, **TR**, `Alloc`>.

### <a name="remarks"></a>Notes

La fonction membre retourne l’adresse de la mémoire tampon de flux stockée de type `pointer` à basic_stringbuf< **elem**, **TR**, `Alloc`>.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="basic_ostringstreamstr"></a><a name="str"></a> basic_ostringstream :: Str

Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Paramètres

*_Newstr*\
La nouvelle chaîne.

### <a name="return-value"></a>Valeur renvoyée

Retourne un objet de classe [basic_string](../standard-library/basic-string-class.md) <  **elem**, **TR**, `Alloc`>, dont la séquence contrôlée est une copie de la séquence contrôlée par **\* ce**.

### <a name="remarks"></a>Notes

La première fonction membre retourne [rdbuf](#rdbuf)  ->  [Str](../standard-library/basic-stringbuf-class.md#str). La deuxième fonction membre appelle `rdbuf`  ->  **Str**( `_Newstr` ).

### <a name="example"></a>Exemple

Consultez [basic_stringbuf :: Str](../standard-library/basic-stringbuf-class.md#str) pour obtenir un exemple qui utilise `str` .

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
