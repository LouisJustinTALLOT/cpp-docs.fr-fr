---
title: Quand dois-je appeler AtlAxWinTerm ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinTerm
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61830023d3fb67d331784769f32cda4eee8355b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360160"
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>Quand dois-je appeler AtlAxWinTerm ?
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) annule l’inscription de le **« AtlAxWin80 »** classe de fenêtre. Vous devez appeler cette fonction (si vous n’avez plus besoin de créer des fenêtres de l’hôte) une fois que toutes les fenêtres hôtes existantes ont été détruits. Si vous n’appelez pas cette fonction, la classe de fenêtre sera annulée automatiquement lorsque le processus se termine.  
  
## <a name="see-also"></a>Voir aussi  
 Quand dois-je appeler AtlAxWinInit  
[Forum aux questions sur la contenance de contrôles](../atl/atl-control-containment-faq.md)

