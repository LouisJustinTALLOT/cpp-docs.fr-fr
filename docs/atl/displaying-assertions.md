---
title: Affichage des Assertions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9133d2fadfa4158eef9755fff7e0d2a62478966
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354277"
---
# <a name="displaying-assertions"></a>Affichage des Assertions
Si le client connecté à votre service semble cesser de répondre, le service peut avoir déclaré et affiche une boîte de message que vous n’êtes pas en mesure de voir. Vous pouvez le vérifier à l’aide du débogueur de Visual C++ pour déboguer votre code (consultez [Gestionnaire des tâches à l’aide de](../atl/using-task-manager.md) plus haut dans cette section).  
  
 Si vous déterminez que votre service affiche une boîte de message qui n’est pas visible, vous souhaitez peut-être définir la **autoriser le Service à interagir avec le bureau** option avant de réutiliser le service. Cette option est un paramètre de démarrage qui permet à tous les messages affichés par le service sur le bureau. Pour définir cette option, ouvrez l’application Services du panneau, sélectionnez le service, cliquez sur **démarrage**, puis sélectionnez le **autoriser le Service à interagir avec le bureau** option.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de débogage](../atl/debugging-tips.md)

