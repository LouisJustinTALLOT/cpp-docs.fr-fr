---
title: -ALLOWISOLATION | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9511ce2d94a426756581b87d863051da25a627b
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42571877"
---
# <a name="allowisolation"></a>/ALLOWISOLATION
Spécifie un comportement pour la recherche de manifeste.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 **/ ALLOWISOLATION** provoque le système d’exploitation et charger des manifestes.  
  
 **/ ALLOWISOLATION** est la valeur par défaut.  
  
 **/ALLOWISOLATION:no** indique que les fichiers exécutables sont chargés comme s’il n’y avait aucun manifeste et causes [référence EDITBIN](../../build/reference/editbin-reference.md) pour définir le `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit dans l’en-tête optional `DllCharacteristics` champ.  
  
 Quand l'isolation est désactivée pour un fichier exécutable, le chargeur Windows ne tente pas de trouver un manifeste d'application pour le processus nouvellement créé. Le nouveau processus n’a pas un contexte d’activation par défaut, même s’il existe un manifeste dans le fichier exécutable lui-même ou s’il existe un manifeste qui porte le nom *nom_exécutable*. exe.manifest.  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)   
 [/ALLOWISOLATION (recherche de manifeste)](../../build/reference/allowisolation-manifest-lookup.md)   
 [Référence des fichiers manifeste](/windows/desktop/SbsCs/manifest-files-reference)