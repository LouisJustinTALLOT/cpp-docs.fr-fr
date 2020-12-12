---
description: 'En savoir plus sur : &lt; strstream&gt;'
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: e99a07df2a63b991232440f8dad0eb299d0e00b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183553"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Définit plusieurs classes qui prennent en charge les opérations iostreams sur les séquences stockées dans un tableau d' **`char`** objets alloué. Ces séquences sont facilement converties vers et à partir de chaînes C.

## <a name="requirements"></a>Spécifications

**En-tête :**\<strstream>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Les objets de type `strstream` fonctionnent avec **`char`** *, qui sont des chaînes C. Utilisez [\<sstream>](../standard-library/sstream.md) pour travailler avec des objets de type [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Les classes dans \<strstream> sont dépréciées. Utilisez plutôt les classes dans \<sstream>.

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[strstreambuf, classe](../standard-library/strstreambuf-class.md)|La classe décrit une mémoire tampon de flux qui contrôle la transmission d’éléments vers et à partir d’une séquence d’éléments stockés dans un **`char`** objet tableau.|
|[istrstream,, classe](../standard-library/istrstream-class.md)|La classe décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|
|[ostrstream, classe](../standard-library/ostrstream-class.md)|La classe décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|
|[strstream, classe](../standard-library/strstream-class.md)|La classe décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|

### <a name="functions"></a>Fonctions

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>Voir aussi

[\<strstream>](../standard-library/strstream.md)\
[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
