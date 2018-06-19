---
title: Puis-je héberger plusieurs contrôles dans une fenêtre unique ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ceb9444b6371e261115bbf52ef5a249100772d1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356422"
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Puis-je héberger plusieurs contrôles dans une fenêtre unique ?
Il n’est pas possible d’héberger plusieurs contrôles dans une seule fenêtre d’hôte ATL. Chaque fenêtre de l’hôte est conçu pour contenir exactement un contrôle à la fois (ainsi, un mécanisme simple pour la gestion des propriétés ambiantes message réflexion et par contrôle). Toutefois, si vous avez besoin de l’utilisateur de voir plusieurs contrôles dans une fenêtre unique, il est très simple pour créer plusieurs fenêtres de l’ordinateur hôte en tant qu’enfants de cette fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions sur la contenance de contrôles](../atl/atl-control-containment-faq.md)

