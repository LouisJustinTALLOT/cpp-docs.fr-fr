---
title: Qu’est un objet hôte ? (ATL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d197f02949f6eaaeee50b428338684135d1db27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357732"
---
# <a name="what-is-a-host-object"></a>Qu’est un objet hôte ?
Un objet hôte est un objet COM qui représente le conteneur de contrôle ActiveX fourni par ATL pour une fenêtre particulière. L’objet hôte sous-classe la fenêtre conteneur afin qu’elle peut refléter les messages au contrôle, il fournit les interfaces de conteneur nécessaires à utiliser par le contrôle, et expose le [interface IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) et [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) interfaces vous permettent de configurer l’environnement du contrôle.  
  
 Vous pouvez utiliser l’objet hôte pour définir les propriétés ambiantes du conteneur.  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions sur la contenance de contrôles](../atl/atl-control-containment-faq.md)

