---
title: Quand dois-je appeler AtlAxWinInit ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinInit
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinInit method
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd9aa1dd14ccae555d4ab9acbbac15e9b66cafe6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360271"
---
# <a name="when-do-i-need-to-call-atlaxwininit"></a>Quand dois-je appeler AtlAxWinInit ?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) enregistre la **« AtlAxWin80 »** classe de fenêtre (plus quelques messages de fenêtre personnalisés) afin que cette fonction doit être appelée avant d’essayer de créer une fenêtre hôte. Toutefois, vous n’ont toujours besoin d’appeler cette fonction explicitement, depuis l’hébergement API (et les classes qui les utilisent) appellent souvent cette fonction pour vous. Il n’existe aucun risque d’appeler cette fonction plusieurs fois. .  
  
## <a name="see-also"></a>Voir aussi  
 Quand dois-je appeler AtlAxWinTerm     
 [Forum aux questions sur la contenance de contrôles](../atl/atl-control-containment-faq.md)
