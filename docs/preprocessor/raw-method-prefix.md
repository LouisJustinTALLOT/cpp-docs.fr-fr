---
title: raw_method_prefix | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 236c9042393e4ff3de57bea83ad566c8b74d5d3b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839918"
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**Spécifique à C++**  
  
 Spécifie un préfixe différent pour éviter les collisions de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Prefix`  
 Le préfixe à utiliser.  
  
## <a name="remarks"></a>Notes  
 Propriétés de bas niveau et les méthodes sont exposées par les fonctions membres nommées avec un préfixe par défaut de **raw_** afin d’éviter les collisions de noms avec les principales fonctions membres de gestion des erreurs.  
  
> [!NOTE]
>  Les effets de la `raw_method_prefix` attribut n’est pas modifié par la présence de la [raw_interfaces_only](#_predir_raw_interfaces_only) attribut. `raw_method_prefix` a toujours la priorité sur `raw_interfaces_only` pour spécifier un préfixe. Si les deux attributs sont utilisés dans la même instruction `#import`, le préfixe spécifié par l'attribut `raw_method_prefix` est utilisé.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)