---
title: auto_rename
ms.date: 11/04/2016
f1_keywords:
- auto_rename
helpviewer_keywords:
- auto_rename attribute
ms.assetid: 1075f3ab-f6fc-4e04-8e22-ebe02695a567
ms.openlocfilehash: 20b971e838488d3e974b393a5e280ca765dac893
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446577"
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