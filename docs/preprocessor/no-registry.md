---
title: no_registry | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_registry
dev_langs:
- C++
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5a3089f71deb4e75aa50b634de84516575d1d02
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807742"
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