---
description: 'En savoir plus sur : classe ostrstream'
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
ms.openlocfilehash: 9966f044d48aa762d681bafcfc22441f7124c9a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305141"
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
|[antigel](#freeze)|Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.|
|[pcount](#pcount)|Retourne le nombre d'éléments écrits dans la séquence contrôlée.|
|[rdbuf](#rdbuf)|Retourne un pointeur vers l'objet `strstreambuf` associé au flux.|
|[str](#str)|Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<strstream>

**Espace de noms :** std

## <a name="ostrstreamfreeze"></a><a name="freeze"></a> ostrstream :: Freeze

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

Consultez [strstream :: Freeze](../standard-library/strstreambuf-class.md#freeze) pour obtenir un exemple qui utilise `freeze` .

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a> ostrstream :: ostrstream

Construit un objet de type `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Mémoire tampon.

*saut*\
Taille de la mémoire tampon en octets.

*_Mode*\
Mode d’entrée et de sortie de la mémoire tampon. Pour plus d’informations, consultez [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="remarks"></a>Notes

Les deux constructeurs initialisent la classe de base en appelant [ostream](../standard-library/ostream-typedefs.md#ostream)(**SB**), où `sb` est l’objet stocké de la classe [strstreambuf](../standard-library/strstreambuf-class.md). Le premier constructeur initialise également `sb` en appelant `strstreambuf` . Le deuxième constructeur initialise la classe de base d’une des deux façons suivantes :

- Si `_Mode`  &  **ios_base :: app**= = 0, vous `ptr` devez désigner le premier élément d’un tableau d' `count` éléments, et le constructeur appelle `strstreambuf` ( `ptr` , `count` , `ptr` ).

- Sinon, `ptr` doit désigner le premier élément d’un tableau d’éléments Count qui contient une chaîne C dont le premier élément est désigné par `ptr` , et le constructeur appelle `strstreambuf` ( `ptr` , `count` , `ptr`  +  `strlen` ( `ptr` )).

## <a name="ostrstreampcount"></a><a name="pcount"></a> ostrstream : nombre de :p

Retourne le nombre d'éléments écrits dans la séquence contrôlée.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments écrits dans la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf)  ->  [pCount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `pcount`, consultez [strstream::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a> ostrstream :: rdbuf

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

## <a name="ostrstreamstr"></a><a name="str"></a> ostrstream :: Str

Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.

```cpp
char *str();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le début de la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf)  ->  [Str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Exemple

Consultez [strstream :: Str](../standard-library/strstreambuf-class.md#str) pour obtenir un exemple qui utilise `str` .

## <a name="see-also"></a>Voir aussi

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
