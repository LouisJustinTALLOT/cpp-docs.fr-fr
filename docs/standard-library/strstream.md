---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: 212223f98db09097e596fc6fe2ddd31bbe16e6b7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245373"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Définit plusieurs classes qui prennent en charge les opérations iostreams sur les séquences stockées dans un tableau alloué de **char** objet. Ces séquences sont facilement converties vers et à partir de chaînes C.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<strstream>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Les objets de type `strstream` fonctionnent avec `char` *, qui sont des chaînes C. Utilisez [\<sstream>](../standard-library/sstream.md) pour les objets de type [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Les classes de \<strstream > sont déconseillés. Envisagez d’utiliser les classes dans \<sstream > à la place.

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|||
|-|-|
|[strstreambuf, classe](../standard-library/strstreambuf-class.md)|La classe décrit une mémoire tampon de flux qui contrôle la transmission d’éléments vers et à partir d’une séquence d’éléments stockés dans un **char** objet tableau.|
|[istrstream, classe](../standard-library/istrstream-class.md)|La classe décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|
|[ostrstream, classe](../standard-library/ostrstream-class.md)|La classe décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|
|[strstream, classe](../standard-library/strstream-class.md)|La classe décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de flux de classe [strstreambuf](../standard-library/strstreambuf-class.md).|

### <a name="functions"></a>Fonctions

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>Voir aussi

[\<strstream>](../standard-library/strstream.md)<br/>
[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
