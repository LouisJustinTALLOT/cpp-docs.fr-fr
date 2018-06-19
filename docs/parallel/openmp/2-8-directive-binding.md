---
title: 2.8 liaison de directives | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02492b228b4bb47a800955f078a59ce680312a87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689452"
---
# <a name="28-directive-binding"></a>2.8 Liaison de directives
Liaison dynamique des directives doit respecter les règles suivantes :  
  
-   Le **pour**, **sections**, **unique**, **master**, et **barrière** directives lier à la dynamique englobant **parallèles**, s’il en existe, quelle que soit la valeur de n’importe quel **si** clause pouvant être présent sur cette directive. Si aucune région parallèle n’est en cours d’exécution, les directives sont exécutées par une équipe composée d’uniquement sur le thread principal.  
  
-   Le **classés** la directive est liée à la dynamique englobante **pour**.  
  
-   Le **atomique** directive applique un accès exclusif au niveau **atomique** directives dans tous les threads, et pas seulement l’équipe actuelle.  
  
-   Le **critique** directive applique un accès exclusif au niveau **critique** directives dans tous les threads, et pas seulement l’équipe actuelle.  
  
-   Une directive ne peut jamais lier dynamiquement à aucune directive en dehors de la plus proche englobant **parallèles**.