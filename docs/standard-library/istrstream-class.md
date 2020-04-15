---
title: istrstream, classe
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: d548a8c2c47a5a345be725afdedb47524344f720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337523"
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
|[Str](#str)|Appelle [freeze](../standard-library/strstreambuf-class.md#freeze), puis retourne un pointeur vers le début de la séquence contrôlée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<strstream>

**Espace de noms :** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a>istrstream::istrstream

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

*Compter*\
La longueur du tampon (*ptr*).

*Ptr*\
Contenu avec lequel la mémoire tampon est initialisée.

### <a name="remarks"></a>Notes

Tous les constructeurs initialisent la classe de base `sb` en appelant [istream](../standard-library/istream-typedefs.md#istream)( sb ), où est**l’objet**stocké de la classe [strstreambuf](../standard-library/strstreambuf-class.md). Les deux premiers constructeurs `sb` sont `strstreambuf`également parastérisants en appelant ( ( **const** `char` \*) `ptr`, 0 ). Les deux autres constructeurs `strstreambuf`appellent plutôt ( ( **const** `char` ) `ptr`, `count` .

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a>istrstream::rdbuf

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

## <a name="istrstreamstr"></a><a name="str"></a>istrstream::str

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

[istream (en)](../standard-library/istream-typedefs.md#istream)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
