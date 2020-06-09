---
title: Méthode d'appel de votre code par le Framework
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: 318ca9558d705ca483d41867a1fe2ad46c36666f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622604"
---
# <a name="how-the-framework-calls-your-code"></a>Méthode d'appel de votre code par le Framework

Il est essentiel de comprendre la relation entre votre code source et le code dans l’infrastructure MFC. Lorsque votre application s’exécute, la majeure partie du déroulement du contrôle réside dans le code du Framework. L’infrastructure gère la boucle de message qui obtient les messages de Windows lorsque l’utilisateur choisit des commandes et modifie les données dans une vue. Les événements que l’infrastructure peut gérer en soi ne s’appuient pas sur votre code. Par exemple, le Framework sait comment fermer des fenêtres et comment quitter l’application en réponse aux commandes de l’utilisateur. Au fur et à mesure qu’il gère ces tâches, l’infrastructure utilise des gestionnaires de messages et des fonctions virtuelles C++ pour vous donner la possibilité de répondre à ces événements également. Votre code n’est toutefois pas dans le contrôle ; le Framework est.

Le Framework appelle votre code pour les événements spécifiques à l’application. Par exemple, quand l’utilisateur choisit une commande de menu, l’infrastructure route la commande le long d’une séquence d’objets C++ : la fenêtre en cours et la fenêtre frame, le document associé à la vue, le modèle de document du document et l’objet application. Si l’un de ces objets peut gérer la commande, il le fait en appelant la fonction de gestionnaire de messages appropriée. Pour une commande donnée, le code appelé peut être le vôtre ou le du Framework.

Cette organisation est quelque peu familière aux programmeurs expérimentés avec la programmation traditionnelle pour Windows ou la programmation pilotée par les événements.

Dans les rubriques connexes, vous allez lire ce que fait l’infrastructure lors de son initialisation et de l’exécution de l’application, puis le nettoyage au fur et à mesure de l’arrêt de l’application. Vous comprendrez également l’emplacement du code que vous écrivez.

Pour plus d’informations, consultez [la classe CWinApp : classe d’application](cwinapp-the-application-class.md) et [modèles de document et processus de création de document/vue](document-templates-and-the-document-view-creation-process.md).

## <a name="see-also"></a>Voir aussi

[Génération sur le Framework](building-on-the-framework.md)
