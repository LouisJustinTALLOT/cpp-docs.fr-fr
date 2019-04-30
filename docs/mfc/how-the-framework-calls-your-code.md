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
ms.openlocfilehash: 81b0749167391a841badff5494023a2ca5d3147e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407950"
---
# <a name="how-the-framework-calls-your-code"></a>Méthode d'appel de votre code par le Framework

Il est essentiel de comprendre la relation entre votre code source et le code dans l’infrastructure MFC. Lorsque votre application s’exécute, la plupart des flux de contrôle se trouve dans le code de l’infrastructure. Le framework gère la boucle de message qui obtient des messages à partir de Windows quand l’utilisateur choisit des commandes et modifie des données dans une vue. Événements de l’infrastructure peut gérer lui-même ne comptent pas du tout sur votre code. Par exemple, le framework sait comment fermer les fenêtres et quitter l’application en réponse aux commandes de l’utilisateur. Comme il gère ces tâches, l’infrastructure utilise des gestionnaires de messages et des fonctions virtuelles C++ pour vous donner la possibilité de répondre à ces événements. Votre code n’est pas dans le contrôle, toutefois ; l’infrastructure est.

L’infrastructure appelle votre code pour les événements spécifiques à l’application. Par exemple, quand l’utilisateur choisit une commande de menu, l’infrastructure achemine la commande le long d’une séquence d’objets C++ : la fenêtre de vue et frame actuelle, le document associé à la vue, le modèle de document et l’objet d’application. Si un de ces objets peut gérer la commande, il fait, en appelant la fonction de gestionnaire de messages approprié. Pour toute commande donnée, le code appelé peut être la vôtre, ou il peut être de l’infrastructure.

Cette disposition est quelque peu familier aux programmeurs ayant l’expérience programmation traditionnelle pour Windows ou de la programmation pilotée par événements.

Rubriques connexes, lit ce que l’infrastructure telle qu’elle initialise et exécute l’application et puis nettoie comme l’application se termine. Vous comprendrez également où intègre le code que vous écrivez.

Pour plus d’informations, consultez [classe CWinApp : La classe Application](../mfc/cwinapp-the-application-class.md) et [modèles de Document et le processus de création de Document/vue](../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="see-also"></a>Voir aussi

[Génération à partir du Framework](../mfc/building-on-the-framework.md)
