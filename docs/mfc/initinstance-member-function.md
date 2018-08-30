---
title: InitInstance, fonction membre | Microsoft Docs
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
ms.openlocfilehash: d026665a48d038092031bf4b632b7ef676124196
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198173"
---
# <a name="initinstance-member-function"></a>InitInstance, fonction membre
Le système d’exploitation Windows vous permet d’exécuter plusieurs copies, ou « instance » de la même application. `WinMain` appels [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) chaque fois qu’une nouvelle instance de l’application démarre.  
  
 La norme `InitInstance` implémentation créée par l’Assistant Application MFC effectue les tâches suivantes :  
  
-   En tant qu’action centrale, crée les modèles de document qui à leur tour créent des documents, vues et fenêtres frame. Pour obtenir une description de ce processus, consultez [création du modèle de Document](../mfc/document-template-creation.md).  
  
-   Charge les options de fichier standard à partir d’un fichier .ini ou le Registre Windows, y compris les noms des fichiers récemment utilisés.  
  
-   Inscrit un ou plusieurs modèles de document.  
  
-   Pour une application MDI, crée une fenêtre frame principale.  
  
-   Traite la ligne de commande pour ouvrir un document spécifié sur la ligne de commande ou pour ouvrir un nouveau document vide.  
  
 Vous pouvez ajouter votre propre code d’initialisation ou modifier le code écrit par l’Assistant.  
  
> [!NOTE]
>  Les applications MFC doivent être initialisées en tant que thread unique cloisonné (STA). Si vous appelez [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) dans votre `InitInstance` substituer, spécifiez COINIT_APARTMENTTHREADED (plutôt que COINIT_MULTITHREADED). Pour plus d’informations, consultez PRB : Application MFC cesse de répondre lorsque vous initialisez l’Application comme un multithread cloisonné (828643) à [ http://support.microsoft.com/default.aspxscid=kb; en-us ; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Voir aussi  
 [CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)
