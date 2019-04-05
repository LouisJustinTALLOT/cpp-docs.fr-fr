---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 7b3917a7114ca44d092f10a7831bb35bc64e9387
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039871"
---
# <a name="renamenamespace"></a>rename_namespace

**Section spécifique à C++**

Renomme l'espace de noms qui contient le contenu de la bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```
rename_namespace("NewName")
```

### <a name="parameters"></a>Paramètres

*NouveauNom*<br/>
Nom du nouvel espace de noms.

## <a name="remarks"></a>Notes

Il accepte un seul argument, *NewName*, qui spécifie le nouveau nom de l’espace de noms.

Pour supprimer l’espace de noms, utilisez le [no_namespace](../preprocessor/no-namespace.md) attribut à la place.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)