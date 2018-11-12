---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: d4e55d06bef823d28c5deb3467654bc530a3853e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456782"
---
# <a name="noimplementation"></a>no_implementation
**Spécifique à C++**

Supprime la génération de l'en-tête .tli, qui contient les implémentations des fonctions membres de wrapper.

## <a name="syntax"></a>Syntaxe

```
no_implementation
```

## <a name="remarks"></a>Notes

Si cet attribut est spécifié, l'en-tête .tlh, avec les déclarations pour exposer les éléments de bibliothèque de types, sera généré sans instruction `#include` pour inclure le fichier d'en-tête .tli.

Cet attribut est utilisé conjointement avec [implementation_only](../preprocessor/implementation-only.md).

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)