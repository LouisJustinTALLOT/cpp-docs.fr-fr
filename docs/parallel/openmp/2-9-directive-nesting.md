---
title: 2.9 imbrication | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28e690ba531b4b37973bc2555d904317181ff918
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691337"
---
# <a name="29-directive-nesting"></a>2.9 Imbrication de directives
L’imbrication de directives dynamique doit respecter les règles suivantes :  
  
-   A **parallèles** directive dynamiquement à l’intérieur d’un autre **parallèles** logiquement établit une nouvelle équipe, qui est constituée du thread actuel uniquement, à moins qu’imbriqués de parallélisme est activée.  
  
-   **pour**, **sections**, et **unique** directives qui lient à la même **parallèles** ne sont pas autorisés à être imbriqués les uns des autres.  
  
-   **critique** directives portant le même nom ne sont pas autorisés à être imbriqués les uns des autres. Notez que cette restriction n’est pas suffisante pour empêcher tout interblocage.  
  
-   **pour**, **sections**, et **unique** directives ne sont pas autorisés dans l’étendue dynamique de **critique**, **classés**, et **master** régions si les directives de lier à la même **parallèles** en tant que les régions.  
  
-   **BARRIÈRE** directives ne sont pas autorisés dans l’étendue dynamique de **pour**, **classés**, **sections**, **unique**, **master**, et **critique** régions si les directives de lier à la même **parallèles** en tant que les régions.  
  
-   **maître** directives ne sont pas autorisés dans l’étendue dynamique de **pour**, **sections**, et **unique** directives si le **master** directives lier à la même **parallèles** en tant que les directives de partage de travail.  
  
-   **classés** directives ne sont pas autorisés dans l’étendue dynamique de **critique** régions si les directives de lier à la même **parallèles** en tant que les régions.  
  
-   Aucune directive est autorisé lors de l’exécution dynamiquement à l’intérieur d’une région parallèle est également autorisé lors de l’exécution en dehors d’une région parallèle. Lors de l’exécution dynamiquement en dehors d’une région parallèle spécifié par l’utilisateur, la directive est exécutée par une équipe composée d’uniquement sur le thread principal.