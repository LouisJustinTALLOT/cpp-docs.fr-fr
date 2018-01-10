---
title: Renommer (#import) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Rename
dev_langs: C++
helpviewer_keywords: rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe5efd48867d5911a6512c32c3e91d80201d03ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="rename-import"></a>rename (#import)
**Spécifique à C++**  
  
 Offre une solution de contournement pour les problèmes de collisions de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
rename("OldName","NewName")  
```  
  
#### <a name="parameters"></a>Paramètres  
 `OldName`  
 Ancien nom dans la bibliothèque de types.  
  
 `NewName`  
 Nom à utiliser au lieu de l'ancien nom.  
  
## <a name="remarks"></a>Notes  
 Si cet attribut est spécifié, le compilateur remplace toutes les occurrences de *OldName* dans une bibliothèque de types avec fournie par l’utilisateur *NewName* dans les fichiers d’en-tête résultant.  
  
 Cet attribut peut être utilisé lorsqu'un nom de la bibliothèque de types coïncide avec une définition de macro dans les fichiers d'en-tête du système. Si cette situation n’est pas résolue, diverses erreurs de syntaxe seront générés, tel que [erreur du compilateur C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) et [erreur du compilateur C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).  
  
> [!NOTE]
>  Le remplacement concerne un nom utilisé dans la bibliothèque de types et pas un nom utilisé dans le fichier d'en-tête résultant.  
  
 Par exemple, supposons qu'une propriété nommée `MyParent` existe dans une bibliothèque de types et qu'une macro `GetMyParent` est définie dans un fichier d'en-tête et utilisée avant `#import`. Étant donné que `GetMyParent` est le nom par défaut d’une fonction wrapper pour la gestion des erreurs **obtenir** propriété, une collision de nom se produit. Pour contourner le problème, utilisez l'attribut suivant dans l'instruction `#import` :  
  
```  
rename("MyParent","MyParentX")  
```  
  
 ce qui renomme le nom `MyParent` dans la bibliothèque de types. Une tentative de changement du nom du wrapper `GetMyParent` échoue :  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
 Cela provient du fait que le nom `GetMyParent` se produit uniquement dans le fichier d'en-tête de bibliothèque de types résultant.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)