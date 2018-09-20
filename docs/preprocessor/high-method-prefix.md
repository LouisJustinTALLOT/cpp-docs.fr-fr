---
title: high_method_prefix | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- high_method_prefix attribute
ms.assetid: cacebf09-12f5-4919-ad40-939e206e340c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 883f573100c31fab8cc0142d371f6a8a14f8783f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428718"
---
# <a name="highmethodprefix"></a>high_method_prefix
**Spécifique à C++**  
  
Spécifie un préfixe à utiliser pour nommer les propriétés et les méthodes de haut niveau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
high_method_prefix("Prefix")  
```  
  
### <a name="parameters"></a>Paramètres  
*Prefix*  
Préfixe à utiliser.  
  
## <a name="remarks"></a>Notes  
 
Par défaut, les propriétés de gestion des erreurs et les méthodes de niveau supérieur sont exposées par des fonctions membres nommées sans préfixe. Les noms sont issus de la bibliothèque de types.  
  
**FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 
[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)