---
title: istrstream, classe
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 37118772f7cefd6f380ceb01908da55500ee7ab5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228230"
---
# <a name="istrstream-class"></a>istrstream, classe

Décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Notes

L'objet stocke un objet de classe `strstreambuf`.

> [!NOTE]
> Cette classe est déconseillée. Utilisez plutôt [istringstream](../standard-library/sstream-typedefs.md#istringstream) ou [wistringstream](../standard-library/sstream-typedefs.md#wistringstream).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[istrstream](#istrstream)|Construit un objet de type `istrstream`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[rdbuf](#rdbuf)|Retourne un pointeur vers l'objet `strstreambuf` associé au flux.|
|[str](#str)|Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<strstream>

**Espace de noms :** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a>istrstream, :: istrstream,

Construit un objet de type `istrstream`.

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>Paramètres

*saut*\
Longueur de la mémoire tampon (*ptr*).

*effectués*\
Contenu avec lequel la mémoire tampon est initialisée.

### <a name="remarks"></a>Notes

Tous les constructeurs initialisent la classe de base en appelant [IStream](../standard-library/istream-typedefs.md#istream)(**SB**), où `sb` est l’objet stocké de la classe [strstreambuf](../standard-library/strstreambuf-class.md). Les deux premiers constructeurs s’initialisent également `sb` en appelant `strstreambuf( ( const char *) ptr, 0 )` . Les deux constructeurs restants appellent à la place `strstreambuf( ( const char *) ptr, count )` .

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a>istrstream, :: rdbuf

Retourne un pointeur vers l’objet strstreambuf associé au flux.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet strstreambuf associé au flux.

### <a name="remarks"></a>Notes

La fonction membre retourne l’adresse de la mémoire tampon de flux stockée de type pointeur vers [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `rdbuf`, consultez [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount).

## <a name="istrstreamstr"></a><a name="str"></a>istrstream, :: Str

Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.

```cpp
char *str();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le début de la séquence contrôlée.

### <a name="remarks"></a>Notes

La fonction membre retourne [rdbuf](#rdbuf)  ->  [Str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Exemple

Consultez [strstream :: Str](../standard-library/strstreambuf-class.md#str) pour obtenir un exemple qui utilise `str` .

## <a name="see-also"></a>Voir aussi

[IStream](../standard-library/istream-typedefs.md#istream)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
