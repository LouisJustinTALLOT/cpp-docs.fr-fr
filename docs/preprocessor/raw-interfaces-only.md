---
title: raw_interfaces_only | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4643181bf70bc92f4ef5e88b8a9add1ba7bdaad7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849299"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**Spécifique à C++**  
  
 Supprime la génération de fonctions wrapper de gestion des erreurs et [propriété](../cpp/property-cpp.md) déclarations qui utilisent ces fonctions wrapper.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>Notes  
 L'attribut `raw_interfaces_only` entraîne également la suppression du préfixe par défaut utilisé dans l'attribution de nom des fonctions qui ne sont pas une propriété. Normalement, le préfixe est **raw_**. Si cet attribut est spécifié, les noms de fonctions proviennent directement de la bibliothèque de types.  
  
 Cet attribut vous permet d'exposer uniquement le contenu de bas niveau de la bibliothèque de types.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)