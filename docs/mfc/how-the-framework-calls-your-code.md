---
title: Comment le Framework appelle votre Code | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f746ce3c3d658ab1dccc098939410b52d91b1188
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348177"
---
# <a name="how-the-framework-calls-your-code"></a>Méthode d'appel de votre code par le Framework
Il est essentiel de comprendre la relation entre votre code source et le code dans l’infrastructure MFC. Lorsque votre application s’exécute, la plupart des flux de contrôle se trouve dans le code de l’infrastructure. Le framework gère la boucle de messages qui Récupère les messages à partir de Windows que l’utilisateur choisit des commandes et modifie des données dans une vue. Événements de l’infrastructure peut gérer en lui-même ne comptent pas du tout sur votre code. Par exemple, l’infrastructure sait comment fermer les fenêtres et quitter l’application en réponse aux commandes de l’utilisateur. Quand elle gère ces tâches, l’infrastructure utilise des gestionnaires de messages et des fonctions virtuelles C++ pour vous donner la possibilité de répondre à ces événements. Votre code n’est pas dans le contrôle est de l’infrastructure.  
  
 L’infrastructure appelle votre code pour les événements spécifiques à l’application. Par exemple, lorsque l’utilisateur choisit une commande de menu, l’infrastructure achemine la commande le long d’une séquence d’objets C++ : la fenêtre de vue et frame actuelle, le document associé à la vue, le modèle de document et l’objet d’application. Si un de ces objets peut gérer la commande, elle fait, en appelant la fonction gestionnaire de messages approprié. Pour une commande particulière, le code appelé peut être le vôtre, ou il peut être de l’infrastructure.  
  
 Cette disposition est quelque peu familier aux programmeurs expérimentés en programmation classique pour Windows ou de la programmation pilotée par événements.  
  
 Rubriques connexes, lit ce que l’infrastructure telle qu’elle initialise exécute l’application et nettoie ensuite que l’application se termine. Vous comprendrez aussi où le code que vous écrivez se situe.  
  
 Pour plus d’informations, consultez [classe CWinApp : la classe d’Application](../mfc/cwinapp-the-application-class.md) et [modèles de Document et le processus de création de Document/vue](../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Génération à partir du Framework](../mfc/building-on-the-framework.md)

