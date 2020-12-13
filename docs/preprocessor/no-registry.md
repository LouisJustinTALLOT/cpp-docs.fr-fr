---
description: 'En savoir plus sur les éléments suivants : no_registry l’attribut import'
title: no_registry l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: fa33bf8096a92ec248b0a9d56e39fcc82f433206
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333295"
---
# <a name="no_registry-import-attribute"></a>no_registry l’attribut d’importation

**no_registry** indique au compilateur de ne pas rechercher dans le registre les bibliothèques de types importées avec `#import` .

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **no_registry**

### <a name="parameters"></a>Paramètres

*bibliothèque de types*\
Bibliothèque de types.

## <a name="remarks"></a>Notes

Si une bibliothèque de types référencée est introuvable dans les répertoires Include, la compilation échoue même si la bibliothèque de types se trouve dans le registre.  **no_registry** se propage à d’autres bibliothèques de types importées implicitement avec `auto_search` .

Le compilateur ne recherche jamais dans le registre les bibliothèques de types spécifiées par le nom de fichier et transmises directement à `#import` .

Lorsque `auto_search` est spécifié, les `#import` directives supplémentaires sont générées à l’aide du paramètre **no_registry** du initial `#import` . Si la `#import` directive initiale était **no_registry**, un `auto_search` généré `#import` est également **no_registry**.

**no_registry** est utile si vous souhaitez importer des bibliothèques de types à références croisées. Il empêche le compilateur de trouver une version antérieure du fichier dans le registre. **no_registry** est également utile si la bibliothèque de types n’est pas inscrite.

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
