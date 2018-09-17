---
title: strstream, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b321891bc5b9392fffc72ec0c9661a39a5631e5a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717832"
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
> Cette classe est dépréciée. Utilisez plutôt [stringstream](../standard-library/sstream-typedefs.md#stringstream) ou [wstringstream](../standard-library/sstream-typedefs.md#wstringstream).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[strstream](#strstream)|Construit un objet de type `strstream`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[freeze](#freeze)|Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.|
|[pcount](#pcount)|Retourne le nombre d'éléments écrits dans la séquence contrôlée.|
|[rdbuf](#rdbuf)|Retourne un pointeur vers l'objet `strstreambuf` associé au flux.|
|[str](#str)|Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<strstream>

**Espace de noms :** std

## <a name="freeze"></a>  strstream::freeze

Fait en sorte qu'une mémoire tampon de flux soit indisponible via des opérations de mémoire tampon de flux.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Paramètres

*_Freezeit*<br/>
Un **bool** indiquant si vous souhaitez que le flux soit gelé.

### <a name="remarks"></a>Notes

La fonction membre appelle [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Exemple

Consultez [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) pour obtenir un exemple qui utilise `freeze`.

## <a name="pcount"></a>  strstream::pcount

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

## <a name="rdbuf"></a>  strstream::rdbuf

Retourne un pointeur vers l’objet strstreambuf associé au flux.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet strstreambuf associé au flux.

### <a name="remarks"></a>Notes

La fonction membre retourne l’adresse de la mémoire tampon de flux stockée de type `pointer` à [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `rdbuf`, consultez [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="str"></a>  strstream::str

Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.

```cpp
char *str();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le début de la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Exemple

Consultez [strstreambuf::str](../standard-library/strstreambuf-class.md#str) pour obtenir un exemple qui utilise `str`.

## <a name="strstream"></a>  strstream::strstream

Construit un objet de type `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*count*<br/>
Taille de la mémoire tampon.

*Mode _De*<br/>
Mode d’entrée et de sortie de la mémoire tampon. Pour plus d’informations, consultez [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*ptr*<br/>
Mémoire tampon.

### <a name="remarks"></a>Notes

Les deux constructeurs initialisent la classe de base en appelant [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**), où `sb` est l’objet stocké de classe [strstreambuf](../standard-library/strstreambuf-class.md). Le premier constructeur initialise également `sb` en appelant [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Le deuxième constructeur initialise la classe de base d’une des deux façons suivantes :

- Si `_Mode`  &  **ios_base::app**== 0, puis *ptr* doit désigner le premier élément d’un tableau de `count` éléments et le constructeur appelle `strstreambuf`( `ptr`, `count`, `ptr`).

- Sinon, *ptr* doit désigner le premier élément d’un tableau d’éléments count qui contient une chaîne C dont le premier élément est désigné par *ptr*et le constructeur appelle `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).

## <a name="see-also"></a>Voir aussi

[iostream](../standard-library/istream-typedefs.md#iostream)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
