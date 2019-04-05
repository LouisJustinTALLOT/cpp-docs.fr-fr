---
title: high_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 3f8975ec9737e02bb1216166cc6c241549e95a07
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029367"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes

**Section spécifique à C++**

Spécifie d'autres préfixes pour trois méthodes de propriété.

## <a name="syntax"></a>Syntaxe

```
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Paramètres

*GetPrefix*<br/>
Préfixe à utiliser pour le `propget` méthodes.

*PutPrefix*<br/>
Préfixe à utiliser pour le `propput` méthodes.

*PutRefPrefix*<br/>
Préfixe à utiliser pour le `propputref` méthodes.

## <a name="remarks"></a>Notes

Par défaut, la gestion des erreurs générales `propget`, `propput`, et `propputref` méthodes sont exposées par les fonctions membres nommées avec les préfixes `Get`, `Put`, et `PutRef`, respectivement.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)