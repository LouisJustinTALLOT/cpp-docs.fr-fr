---
description: 'En savoir plus sur : affichage des assertions'
title: Affichage des assertions
ms.date: 05/05/2019
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: 3f925d5f3a7d1ad0ac1171ea8983b57ead147bf4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153012"
---
# <a name="displaying-assertions"></a>Affichage des assertions

Si le client connecté à votre service semble cesser de répondre, le service a peut-être déclaré et affiché une boîte de message que vous ne pouvez pas voir. Vous pouvez le vérifier en utilisant le débogueur Visual Studio pour déboguer votre code (consultez [utilisation du gestionnaire des tâches](../atl/using-task-manager.md) plus haut dans cette section).

Si vous déterminez que votre service affiche une boîte de message que vous ne voyez pas, vous pouvez définir l’option **autoriser le service à interagir avec le bureau** avant de réutiliser le service. Cette option est un paramètre de démarrage qui permet à toutes les boîtes de message affichées par le service de s’afficher sur le bureau. Pour définir cette option, ouvrez l’application services du panneau de configuration, sélectionnez le service, cliquez sur **démarrage**, puis sélectionnez l’option **autoriser le service à interagir avec le bureau** .

## <a name="see-also"></a>Voir aussi

[Conseils de débogage](../atl/debugging-tips.md)
