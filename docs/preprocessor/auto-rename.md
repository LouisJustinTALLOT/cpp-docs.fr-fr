---
title: auto_rename
ms.date: 11/04/2016
f1_keywords:
- auto_rename
helpviewer_keywords:
- auto_rename attribute
ms.assetid: 1075f3ab-f6fc-4e04-8e22-ebe02695a567
ms.openlocfilehash: ba07b8532ba64c99f835e59d7c71aac8e3f2b03d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336684"
---
# <a name="autorename"></a>auto_rename

**Spécifique à C++**

Renomme des mots réservés C++ en ajoutant deux traits de soulignement (__) au nom de variable pour résoudre les conflits potentiels entre les noms.

## <a name="syntax"></a>Syntaxe

```
auto_rename
```

## <a name="remarks"></a>Notes

Cet attribut est utilisé lors de l'importation d'une bibliothèque de types qui utilise un ou plusieurs mots réservés C++ (mots clés ou macros) comme noms de variables.

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)