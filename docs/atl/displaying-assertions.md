---
title: Affichage des Assertions
ms.date: 05/05/2019
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: 962a33a7d5d922f7f1655e22b2c9d0acdcf8925c
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221264"
---
# <a name="displaying-assertions"></a>Affichage des Assertions

Si le client connecté à votre service semble cesser de répondre, le service peut avoir déclaré et affiche une boîte de message que vous n’êtes pas en mesure de voir. Vous pouvez le vérifier à l’aide du débogueur Visual Studio pour déboguer votre code (consultez [Gestionnaire des tâches à l’aide de](../atl/using-task-manager.md) plus haut dans cette section).

Si vous déterminez que votre service affiche une boîte de message que vous ne voyez pas, il pourrez que vous souhaitez définir le **autoriser le Service à interagir avec le bureau** option avant d’utiliser le service à nouveau. Cette option est un paramètre de démarrage qui autorise des boîtes de message affichés par le service sur le bureau. Pour définir cette option, ouvrez l’application Services du panneau, sélectionnez le service, cliquez sur **démarrage**, puis sélectionnez le **autoriser le Service à interagir avec le bureau** option.

## <a name="see-also"></a>Voir aussi

[Conseils de débogage](../atl/debugging-tips.md)
