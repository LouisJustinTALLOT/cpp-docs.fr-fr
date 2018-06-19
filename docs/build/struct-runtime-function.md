---
title: RUNTIME_FUNCTION, structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c2f28380d4a14cf7617653ede20468c45649a8b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379924"
---
# <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION, structure
Gestion des exceptions basée sur une table requiert une entrée de table pour toutes les fonctions allouer de l’espace de pile ou d’appeler une autre fonction (par exemple, les fonctions non-feuille). Entrées de la table (fonction) ont le format suivant :  
  
|||  
|-|-|  
|ULONG|Adresse de début (fonction)|  
|ULONG|Adresse de fin (fonction)|  
|ULONG|Adresse des informations de déroulement|  
  
 La structure RUNTIME_FUNCTION doit être DWORD aligné en mémoire. Toutes les adresses sont relatives à l’image, autrement dit, ils sont des décalages de 32 bits à partir de l’adresse de départ de l’image qui contient l’entrée de fonction table. Ces entrées sont triées et placées dans la section .pdata d’une image PE32 +. Pour les fonctions générées dynamiquement [compilateurs JIT], le runtime pour prendre en charge ces fonctions doit utiliser RtlInstallFunctionTableCallback ou RtlAddFunctionTable pour fournir ces informations pour le système d’exploitation. Cela entraîne non fiable gestion des exceptions et débogage de processus.  
  
## <a name="see-also"></a>Voir aussi  
 [Données de déroulement pour la gestion des exceptions et la prise en charge du débogueur](../build/unwind-data-for-exception-handling-debugger-support.md)