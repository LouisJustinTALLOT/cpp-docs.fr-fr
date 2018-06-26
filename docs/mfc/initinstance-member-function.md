---
title: InitInstance, fonction membre | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9379fef6a1d676d6a3bc757ee51d5d27acd5f6f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930174"
---
# <a name="initinstance-member-function"></a>InitInstance, fonction membre
Le système d’exploitation Windows vous permet d’exécuter plusieurs copies, ou « instance », de la même application. `WinMain` appels [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) chaque fois qu’une nouvelle instance de l’application démarre.  
  
 La norme `InitInstance` implémentation créée par l’Assistant Application MFC effectue les tâches suivantes :  
  
-   En tant qu’action centrale, crée les modèles de document qui à leur tour créent des documents, vues et fenêtres frame. Pour obtenir une description de ce processus, consultez [création d’un modèle de Document](../mfc/document-template-creation.md).  
  
-   Charge les options de fichiers standard à partir d’un fichier .ini ou du Registre Windows, y compris les noms des fichiers récemment utilisés.  
  
-   Inscrit un ou plusieurs modèles de document.  
  
-   Pour une application MDI, crée une fenêtre frame principale.  
  
-   Traite la ligne de commande pour ouvrir un document spécifié sur la ligne de commande ou pour ouvrir un nouveau document vide.  
  
 Vous pouvez ajouter votre propre code d’initialisation ou modifier le code écrit par l’Assistant.  
  
> [!NOTE]
>  Les applications MFC doivent être initialisées dans un thread unique cloisonné (STA). Si vous appelez [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) dans votre `InitInstance` remplacer, spécifiez COINIT_APARTMENTTHREADED (plutôt que COINIT_MULTITHREADED). Pour plus d’informations, consultez PRB : Application MFC ne répond plus lorsque vous initialisez l’Application en tant qu’un multithread cloisonné (828643) à [ http://support.microsoft.com/default.aspxscid=kb; en-us ; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Voir aussi  
 [CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)
