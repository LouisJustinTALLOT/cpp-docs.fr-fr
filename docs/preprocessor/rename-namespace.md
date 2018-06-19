---
title: rename_namespace | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a51114787dde2f858a8409538083282ef292d599
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839389"
---
# <a name="renamenamespace"></a>rename_namespace
**Spécifique à C++**  
  
 Renomme l'espace de noms qui contient le contenu de la bibliothèque de types.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
rename_namespace("NewName")  
```  
  
#### <a name="parameters"></a>Paramètres  
 `NewName`  
 Nom du nouvel espace de noms.  
  
## <a name="remarks"></a>Notes  
 Il accepte un argument unique, *NewName*, qui spécifie le nouveau nom de l’espace de noms.  
  
 Pour supprimer l’espace de noms, utilisez la [no_namespace](../preprocessor/no-namespace.md) d’attribut à la place.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)