---
description: 'En savoir plus sur : classe strstream'
title: strstream, classe
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: c37a2ec46872b34e256710fe61f216a84cb0359d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183527"
---
# <a name="strstream-class"></a>strstream, classe

Décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Notes

L'objet stocke un objet de classe `strstreambuf`.

> [!NOTE]
> Cette classe est déconseillée. Utilisez plutôt [stringstream](../standard-library/sstream-typedefs.md#stringstream) ou [wstringstream](../standard-library/sstream-typedefs.md#wstringstream).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[strstream](#strstream)|Construit un objet de type `strstream`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[antigel](#freeze)|Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.|
|[pcount](#pcount)|Retourne le nombre d'éléments écrits dans la séquence contrôlée.|
|[rdbuf](#rdbuf)|Retourne un pointeur vers l'objet `strstreambuf` associé au flux.|
|[str](#str)|Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<strstream>

**Espace de noms :** std

## <a name="strstreamfreeze"></a><a name="freeze"></a> strstream :: Freeze

Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Paramètres

*_Freezeit*\
**`bool`** Valeur qui indique si vous souhaitez que le flux soit figé.

### <a name="remarks"></a>Notes

La fonction membre appelle [rdbuf](#rdbuf)  ->  [Freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Exemple

Consultez [strstreambuf :: Freeze](../standard-library/strstreambuf-class.md#freeze) pour obtenir un exemple qui utilise `freeze` .

## <a name="strstreampcount"></a><a name="pcount"></a> strstream : nombre de :p

Retourne le nombre d'éléments écrits dans la séquence contrôlée.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments écrits dans la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf)  ->  [pCount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de pcount, consultez [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a> strstream :: rdbuf

Retourne un pointeur vers l’objet strstreambuf associé au flux.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valeur renvoyée

Un pointeur vers l’objet strstreambuf associé au flux.

### <a name="remarks"></a>Notes

La fonction membre retourne l’adresse de la mémoire tampon de flux stockée de type `pointer` à [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `rdbuf`, consultez [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="strstreamstr"></a><a name="str"></a> strstream :: Str

Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.

```cpp
char *str();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le début de la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf)  ->  [Str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Exemple

Consultez [strstreambuf :: Str](../standard-library/strstreambuf-class.md#str) pour obtenir un exemple qui utilise `str` .

## <a name="strstreamstrstream"></a><a name="strstream"></a> strstream :: strstream

Construit un objet de type `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*saut*\
Taille de la mémoire tampon.

*_Mode*\
Mode d’entrée et de sortie de la mémoire tampon. Pour plus d’informations, consultez [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*effectués*\
Mémoire tampon.

### <a name="remarks"></a>Notes

Les deux constructeurs initialisent la classe de base en appelant [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **SB**), où `sb` est l’objet stocké de la classe [strstreambuf](../standard-library/strstreambuf-class.md). Le premier constructeur initialise également `sb` en appelant [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Le deuxième constructeur initialise la classe de base d’une des deux façons suivantes :

- Si `_Mode`  &  **ios_base :: app**= = 0, *ptr* doit désigner le premier élément d’un tableau d' `count` éléments, et le constructeur appelle `strstreambuf` ( `ptr` , `count` , `ptr` ).

- Sinon, *ptr* doit désigner le premier élément d’un tableau d’éléments Count qui contient une chaîne C dont le premier élément est désigné par *ptr*, et le constructeur appelle `strstreambuf` ( `ptr` , `count` , `ptr`  +  `strlen` ( `ptr` )).

## <a name="see-also"></a>Voir aussi

[iostream](../standard-library/istream-typedefs.md#iostream)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
