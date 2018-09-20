---
title: raw_property_prefixes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ae69e26077692188b8e013e949592df26d7701a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420398"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**Spécifique à C++**  
  
Spécifie d'autres préfixes pour trois méthodes de propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>Paramètres  
*GetPrefix*  
Préfixe à utiliser pour le `propget` méthodes.  
  
*PutPrefix*  
Préfixe à utiliser pour le `propput` méthodes.  
  
*PutRefPrefix*  
Préfixe à utiliser pour le `propputref` méthodes.  
  
## <a name="remarks"></a>Notes  
 
Par défaut, de bas niveau `propget`, `propput`, et `propputref` méthodes sont exposées par les fonctions membres nommées avec les préfixes de **get_**, **put_**, et **putref_** respectivement. Ces préfixes sont compatibles avec les noms utilisés dans les fichiers d'en-tête générés par MIDL.  
  
**FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 
[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)