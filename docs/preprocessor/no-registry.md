---
title: no_registry | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_registry
dev_langs:
- C++
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 416663592f4362c110637fb4d4b4b418d9776cde
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849663"
---
# <a name="noregistry"></a>no_registry
`no_registry` indique au compilateur qu'il ne faut pas rechercher dans le Registre les bibliothèques de types importées avec `#import`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#import filename no_registry  
```  
  
#### <a name="parameters"></a>Paramètres  
 *filename*  
 Bibliothèque de types.  
  
## <a name="remarks"></a>Notes  
 Si une bibliothèque de types référencée est introuvable dans les répertoires include, la compilation échoue même si la bibliothèque de types est dans le Registre.  `no_registry` se propage à d’autres bibliothèques de types importées implicitement avec `auto_search`.  
  
 Le compilateur ne recherchera jamais dans le Registre les bibliothèques de types qui sont spécifiées par nom de fichier et passées directement à `#import`.  
  
 Lorsque `auto_search` est spécifié, les  `#import` supplémentaires sont générés avec le paramètre `no_registry` de l'`#import` initial (si la directive `#import` initiale était `no_registry`, un `auto_search` généré par `#import` est également `no_registry`.)  
  
 `no_registry` est utile si vous souhaitez importer des bibliothèques de types référencé croisées sans risque du compilateur recherche une version antérieure du fichier dans le Registre.  `no_registry` est également utile si la bibliothèque de types n’est pas inscrit.  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)