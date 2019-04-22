---
title: no_registry
ms.date: 10/18/2018
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 2a0fd9a761f765aa9562ab18c095f683b80c7987
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023423"
---
# <a name="noregistry"></a>no_registry

**no_registry** indique au compilateur de ne pas rechercher le Registre pour les bibliothèques de types importés avec `#import`.

## <a name="syntax"></a>Syntaxe

```
#import filename no_registry
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Bibliothèque de types.

## <a name="remarks"></a>Notes

Si une bibliothèque de types référencée est introuvable dans les répertoires include, la compilation échoue même si la bibliothèque de types est dans le Registre.  **no_registry** se propage à d’autres bibliothèques de types implicitement importées avec `auto_search`.

Le compilateur ne recherchera jamais dans le Registre les bibliothèques de types qui sont spécifiées par nom de fichier et passées directement à `#import`.

Lorsque `auto_search` est spécifié, supplémentaires `#import`s sera généré avec la **no_registry** paramètre initial `#import` (si initial `#import` directive a été **no_registry** , un `auto_search`-généré `#import` est également **no_registry**.)

**no_registry** est utile si vous souhaitez importer des bibliothèques de types référencée sans le compilateur risque de trouver une version antérieure du fichier dans le Registre. **no_registry** est également utile si la bibliothèque de types n’est pas inscrit.

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)