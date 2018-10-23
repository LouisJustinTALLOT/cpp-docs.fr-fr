---
title: high_property_prefixes | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3932a7632b12120e722c5f375f4387e08f1853b
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809055"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes

**Spécifique à C++**

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

**FIN spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)