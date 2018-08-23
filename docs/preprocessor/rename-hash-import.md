---
title: Renommer (#import) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2930ab9cbc5b847252e20f185b335a547317fa5b
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539994"
---
# <a name="rename-import"></a>rename (#import)
**Spécifique à C++**  
  
Offre une solution de contournement pour les problèmes de collisions de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
rename("OldName","NewName")  
```  
  
### <a name="parameters"></a>Paramètres  
*OldName*  
Ancien nom dans la bibliothèque de types.  
  
*NewName*  
Nom à utiliser au lieu de l'ancien nom.  
  
## <a name="remarks"></a>Notes  
 
Si cet attribut est spécifié, le compilateur remplace toutes les occurrences de *OldName* dans une bibliothèque de types avec fournie par l’utilisateur *NewName* dans les fichiers d’en-tête qui en résulte.  
  
Cet attribut peut être utilisé lorsqu'un nom de la bibliothèque de types coïncide avec une définition de macro dans les fichiers d'en-tête du système. Si cette situation n’est pas résolue, diverses erreurs de syntaxe seront générées, tel que [erreur du compilateur C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) et [erreur du compilateur C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).  
  
> [!NOTE]
> Le remplacement concerne un nom utilisé dans la bibliothèque de types et pas un nom utilisé dans le fichier d'en-tête résultant.  
  
Par exemple, supposons qu'une propriété nommée `MyParent` existe dans une bibliothèque de types et qu'une macro `GetMyParent` est définie dans un fichier d'en-tête et utilisée avant `#import`. Dans la mesure où `GetMyParent` est le nom par défaut d’une fonction wrapper pour la gestion des erreurs `get` propriété, une collision de nom se produit. Pour contourner le problème, utilisez l'attribut suivant dans l'instruction `#import` :  
  
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
[directive #import](../preprocessor/hash-import-directive-cpp.md)