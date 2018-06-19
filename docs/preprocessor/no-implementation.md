---
title: no_implementation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf756a411404d2ebb821d5b226818844acfca75b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849546"
---
# <a name="noimplementation"></a>no_implementation
**Spécifique à C++**  
  
 Supprime la génération de l'en-tête .tli, qui contient les implémentations des fonctions membres de wrapper.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>Notes  
 Si cet attribut est spécifié, l'en-tête .tlh, avec les déclarations pour exposer les éléments de bibliothèque de types, sera généré sans instruction `#include` pour inclure le fichier d'en-tête .tli.  
  
 Cet attribut est utilisé conjointement avec [implementation_only](../preprocessor/implementation-only.md).  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)