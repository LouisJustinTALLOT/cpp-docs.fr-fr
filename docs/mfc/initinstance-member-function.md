---
title: InitInstance, fonction membre
ms.date: 11/04/2016
f1_keywords:
- InitInstance
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
ms.openlocfilehash: 0a458f19f956bb1092cc76acd587bc467f25325e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625581"
---
# <a name="initinstance-member-function"></a>InitInstance, fonction membre

Le système d’exploitation Windows vous permet d’exécuter plusieurs copies, ou « instances », de la même application. `WinMain`appelle [InitInstance](reference/cwinapp-class.md#initinstance) chaque fois qu’une nouvelle instance de l’application démarre.

L' `InitInstance` implémentation standard créée par l’Assistant Application MFC effectue les tâches suivantes :

- Comme action centrale, crée les modèles de document qui, à leur tour, créent des documents, des vues et des fenêtres Frame. Pour obtenir une description de ce processus, consultez Création d’un [modèle de document](document-template-creation.md).

- Charge les options de fichier standard à partir d’un fichier. ini ou du Registre Windows, y compris les noms des derniers fichiers utilisés.

- Inscrit un ou plusieurs modèles de document.

- Pour une application MDI, crée une fenêtre frame principale.

- Traite la ligne de commande pour ouvrir un document spécifié sur la ligne de commande ou pour ouvrir un nouveau document vide.

Vous pouvez ajouter votre propre code d’initialisation ou modifier le code écrit par l’Assistant.

> [!NOTE]
> Les applications MFC doivent être initialisées en tant que thread unique cloisonné (STA). Si vous appelez [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) dans votre `InitInstance` remplacement, spécifiez COINIT_APARTMENTTHREADED (plutôt que COINIT_MULTITHREADED).

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](cwinapp-the-application-class.md)
