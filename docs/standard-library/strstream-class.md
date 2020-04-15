---
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
ms.openlocfilehash: 047b7e9d7fdece75137980b013d43abf1d5e3ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376616"
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
|[Gèlent](#freeze)|Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.|
|[pcount](#pcount)|Retourne le nombre d'éléments écrits dans la séquence contrôlée.|
|[rdbuf](#rdbuf)|Retourne un pointeur vers l'objet `strstreambuf` associé au flux.|
|[Str](#str)|Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<strstream>

**Espace de noms :** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>strstream::gel

Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Paramètres

*_Freezeit*\
Un **bool** indiquant si vous voulez que le flux soit gelé.

### <a name="remarks"></a>Notes

La fonction membre appelle le[gel](../standard-library/strstreambuf-class.md#freeze) [de rdbuf](#rdbuf) ->  *(Gelit*).

### <a name="example"></a>Exemple

Voir [strstreambuf::geler](../standard-library/strstreambuf-class.md#freeze) par `freeze`exemple qui utilise .

## <a name="strstreampcount"></a><a name="pcount"></a>strstream::pcount

Retourne le nombre d'éléments écrits dans la séquence contrôlée.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments écrits dans la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de pcount, consultez [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>strstream::rdbuf

Retourne un pointeur vers l’objet strstreambuf associé au flux.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet strstreambuf associé au flux.

### <a name="remarks"></a>Notes

La fonction membre renvoie l’adresse `pointer` du tampon de flux stocké de type à [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `rdbuf`, consultez [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="strstreamstr"></a><a name="str"></a>strstream::str

Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.

```cpp
char *str();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le début de la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Exemple

Voir [strstreambuf::str](../standard-library/strstreambuf-class.md#str) pour un `str`échantillon qui utilise .

## <a name="strstreamstrstream"></a><a name="strstream"></a>strstream::strstream

Construit un objet de type `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*Compter*\
Taille de la mémoire tampon.

*_Mode*\
Mode d’entrée et de sortie de la mémoire tampon. Pour plus d’informations, consultez [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Ptr*\
Mémoire tampon.

### <a name="remarks"></a>Notes

Les deux constructeurs initialisent la classe de base `sb` en appelant [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( sb ), où est **l’objet**stocké de la classe [strstreambuf](../standard-library/strstreambuf-class.md). Le premier constructeur est `sb` également para initialisé en appelant [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Le deuxième constructeur initialise la classe de base d’une des deux façons suivantes :

- Si `_Mode`  &  **ios_base: :app**0, puis *ptr* doit désigner le premier `count` élément d’un tableau `strstreambuf` `ptr`d’éléments, et les appels constructeurs ( , `count`. `ptr`.

- Sinon, *ptr* doit désigner le premier élément d’un tableau d’éléments de comptage qui contient une `count`chaîne `ptr`  +  `strlen` `ptr`C dont le premier élément est désigné par *ptr*, et les appels `strstreambuf`constructeurs ( `ptr`, , ) .

## <a name="see-also"></a>Voir aussi

[iostream](../standard-library/istream-typedefs.md#iostream)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
