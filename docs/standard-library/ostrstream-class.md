---
title: ostrstream, classe
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: b52ba70607a5214a6aa28f04cdded0b19a56b2f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373544"
---
# <a name="ostrstream-class"></a>ostrstream, classe

Décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux de la classe [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Notes

L'objet stocke un objet de classe `strstreambuf`.

> [!NOTE]
> Cette classe est déconseillée. Utilisez plutôt [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) ou [wostringstream](../standard-library/sstream-typedefs.md#wostringstream).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[ostrstream](#ostrstream)|Construit un objet de type `ostrstream`.|

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

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>ostrstream::gel

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

Voir [strstream::geler](../standard-library/strstreambuf-class.md#freeze) pour `freeze`un exemple qui utilise .

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>ostrstream::ostrstream

Construit un objet de type `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Paramètres

*Ptr*\
Mémoire tampon.

*Compter*\
Taille de la mémoire tampon en octets.

*_Mode*\
Mode d’entrée et de sortie de la mémoire tampon. Pour plus d’informations, consultez [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="remarks"></a>Notes

Les deux constructeurs initialisent la classe de base `sb` en appelant [ostream](../standard-library/ostream-typedefs.md#ostream)( sb ), où est**l’objet**stocké de la classe [strstreambuf](../standard-library/strstreambuf-class.md). Le premier constructeur est `sb` également `strstreambuf`para initialisé en appelant . Le deuxième constructeur initialise la classe de base d’une des deux façons suivantes :

- Si `_Mode`  &  **ios_base : : app**0, `ptr` doit alors désigner le `count` premier élément d’un `strstreambuf``ptr`tableau `count` `ptr`d’éléments, et les appels du constructeur (, , . .

- Sinon, `ptr` doit désigner le premier élément d’un tableau d’éléments de `ptr`comptage qui contient `strstreambuf``ptr`une `count` `ptr`  +  `strlen`chaîne `ptr`C dont le premier élément est désigné par , et les appels constructeurs ( , , ( ) ).

## <a name="ostrstreampcount"></a><a name="pcount"></a>ostrstream::pcount

Retourne le nombre d'éléments écrits dans la séquence contrôlée.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments écrits dans la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `pcount`, consultez [strstream::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>ostrstream::rdbuf

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

## <a name="ostrstreamstr"></a><a name="str"></a>ostrstream::str

Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.

```cpp
char *str();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le début de la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Exemple

Voir [strstream::str](../standard-library/strstreambuf-class.md#str) pour un `str`échantillon qui utilise .

## <a name="see-also"></a>Voir aussi

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
