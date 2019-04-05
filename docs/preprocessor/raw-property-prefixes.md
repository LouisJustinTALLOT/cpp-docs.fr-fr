---
title: raw_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: 23250b524fdaa2181c8e28229ccec680ffdae715
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033253"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes

**Section spécifique à C++**

Spécifie d'autres préfixes pour trois méthodes de propriété.

## <a name="syntax"></a>Syntaxe

```
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Paramètres

*GetPrefix*<br/>
Préfixe à utiliser pour le `propget` méthodes.

*PutPrefix*<br/>
Préfixe à utiliser pour le `propput` méthodes.

*PutRefPrefix*<br/>
Préfixe à utiliser pour le `propputref` méthodes.

## <a name="remarks"></a>Notes

Par défaut, de bas niveau `propget`, `propput`, et `propputref` méthodes sont exposées par les fonctions membres nommées avec les préfixes de **get_**, **put_**, et **putref_** respectivement. Ces préfixes sont compatibles avec les noms utilisés dans les fichiers d'en-tête générés par MIDL.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)