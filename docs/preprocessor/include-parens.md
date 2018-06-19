---
title: Include () | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 756aea4400d98b2bf061a54955b3df4b4eddd993
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849273"
---
# <a name="include"></a>include()
**Spécifique à C++**  
  
 Désactive l'exclusion automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Name1`  
 Premier élément à inclure de force.  
  
 `Name2`  
 Deuxième élément à inclure de force (si nécessaire).  
  
## <a name="remarks"></a>Notes  
 Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. `#import` tente d'éviter les erreurs de définitions multiples en excluant automatiquement ces éléments. Si les éléments ont été exclus, comme indiqué par [l’avertissement du compilateur (niveau 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), et ils ne doivent pas avoir été, cet attribut peut être utilisé pour désactiver l’exclusion automatique. Cet attribut peut comprendre n’importe quel nombre d’arguments, chacun portant le nom de l’élément bibliothèque-types à inclure.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)