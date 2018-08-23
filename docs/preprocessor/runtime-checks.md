---
title: runtime_checks | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
dev_langs:
- C++
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b20ea9dd12bfe4daff8e2e440c96a41c220aa742
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540387"
---
# <a name="runtimechecks"></a>runtime_checks
Désactive ou restaure les paramètres [/RTC](../build/reference/rtc-run-time-error-checks.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma runtime_checks( "[runtime_checks]", {restore | off} )  
```  
  
## <a name="remarks"></a>Notes  
 
Vous ne pouvez pas activer un contrôle à l'exécution qui n'a pas été activé via une option du compilateur. Par exemple, si vous ne spécifiez pas `/RTCs`, en spécifiant `#pragma runtime_checks( "s", restore)` n’activera pas la vérification du frame de pile.  
  
Le pragma **runtime_checks** doit apparaître à l'extérieur d'une fonction et prend effet à la première fonction définie après sa détection. Le *restaurer* et *hors* arguments activer des options spécifiées dans le **runtime_checks** activé ou désactivé.  
  
Le **runtime_checks** peut être zéro ou plusieurs des paramètres indiqués dans le tableau suivant.  
  
### <a name="parameters-of-the-runtimechecks-pragma"></a>Paramètres du pragma runtime_checks  
  
|Paramètre(s)|Type de contrôle à l'exécution|  
|--------------------|-----------------------------|  
|*s*|Active la vérification de pile (frame).|  
|*c*|Signale quand une valeur est assignée à un type de données plus petit qui se traduit par une perte de données.|  
|*u*|Signale quand une variable est utilisée avant d'être définie.|  
  
Ce sont les mêmes lettres que celui utilisés avec la `/RTC` option du compilateur. Exemple :  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
L'utilisation du pragma **runtime_checks** avec la chaîne vide (**""**) est une forme particulière de la directive :  
  
- Lorsque vous utilisez le *hors* paramètre, il trouve sur les vérifications d’erreur d’exécution, répertoriées dans le tableau ci-dessus, off.  
  
- Lorsque vous utilisez le *restaurer* paramètre, il réinitialise les contrôles d’erreurs d’exécution à ceux que vous avez spécifié avec la `/RTC` option du compilateur.  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## <a name="see-also"></a>Voir aussi  
 
[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   