---
title: -GUARD (activer les contrôles de protection) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d05dd4f9d213c3d2729459486a9d0cfdbd79110
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375254"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (activer les contrôles de protection)
Spécifie la prise en charge pour les contrôles de protection du flux de contrôle de l’image exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GUARD:{CF|NO}  
```  
  
## <a name="remarks"></a>Notes  
 Quand /GUARD:CF est spécifié, l'éditeur de liens modifie l'en-tête d'un fichier .dll ou .exe pour indiquer la prise en charge des contrôles d'exécution de la protection du flux de contrôle (CFG). L'éditeur de liens ajoute également les données d'adresse cible du flux de contrôle nécessaire dans l'en-tête. Par défaut, /GUARD:CF est désactivé. Il peut être désactivé explicitement en spécifiant /GUARD:NO. Pour être efficaces, / Guard : CF requiert également le [/DYNAMICBASE (utiliser espace randomisation du format adresse)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) option de l’éditeur de liens, qui est activé par défaut.  
  
 Lorsque le code source est compilé à l’aide de la [/Guard : CF](../../build/reference/guard-enable-control-flow-guard.md) option, le compilateur analyse le flux de contrôle en examinant tous les appels indirects pour les adresses cibles possibles. Le compilateur insère le code pour vérifier que l'adresse cible d'une instruction d'appel indirect figure dans la liste des adresses cibles connues au moment de l'exécution. Les systèmes d'exploitation qui prennent en charge la protection CFG arrêtent tout programme qui ne satisfait pas une vérification à l'exécution CFG. Il est ainsi plus difficile pour un attaquant d'exécuter du code malveillant en recourant à une altération des données pour modifier une cible d'appel.  
  
 L'option /GUARD:CF doit être spécifiée dans le compilateur et l'éditeur de liens pour créer des images exécutables avec protection CFG. Le code qui est compilé, mais pas lié avec l'option /GUARD:CF implique un coût de vérifications à l'exécution, mais n'active pas la protection CFG. Lorsque l’option/Guard : CF est spécifiée dans le `cl` commande pour compiler et lier en une seule étape, le compilateur passe l’indicateur à l’éditeur de liens. Lorsque le **du flux de contrôle** est définie dans Visual Studio, l’option/Guard : CF est passée au compilateur et l’éditeur de liens. Lorsque les fichiers objets ou bibliothèques ont été compilés séparément, l’option doit être spécifiée explicitement dans la `link` commande.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez **propriétés de Configuration**, **l’éditeur de liens**, **ligne de commande**.  
  
3.  Dans **des Options supplémentaires**, entrez `/GUARD:CF`.  
  
## <a name="see-also"></a>Voir aussi  
 [/Guard (activer le contrôle de la protection du flux)](../../build/reference/guard-enable-control-flow-guard.md)   
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)