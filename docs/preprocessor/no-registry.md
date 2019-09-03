---
title: no_registry importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 7c81cc2f570cb9ac4e977dac6d55cb69e491d3b2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220723"
---
# <a name="no_registry-import-attribute"></a>no_registry importer l’attribut

**no_registry** indique au compilateur de ne pas rechercher dans le registre les bibliothèques de `#import`types importées avec.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **no_registry**

### <a name="parameters"></a>Paramètres

*bibliothèque de types*\
Bibliothèque de types.

## <a name="remarks"></a>Notes

Si une bibliothèque de types référencée est introuvable dans les répertoires Include, la compilation échoue même si la bibliothèque de types se trouve dans le registre.  **no_registry** se propage à d’autres bibliothèques de types importées implicitement avec `auto_search`.

Le compilateur ne recherche jamais dans le registre les bibliothèques de types spécifiées par le nom de fichier `#import`et transmises directement à.

Lorsque `auto_search` est spécifié, les directives `#import` supplémentaires sont générées à l’aide du paramètre **no_registry** du `#import`initial. Si la directive `#import` initiale était **no_registry**, un `auto_search`-generated `#import` est également **no_registry**.

**no_registry** est utile si vous souhaitez importer des bibliothèques de types à références croisées. Il empêche le compilateur de trouver une version antérieure du fichier dans le registre. **no_registry** est également utile si la bibliothèque de types n’est pas inscrite.

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
