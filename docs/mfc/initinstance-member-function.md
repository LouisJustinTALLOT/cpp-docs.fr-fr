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
ms.openlocfilehash: 2cf5b266348e299fe761ba40bd2cfb849f02b9ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377192"
---
# <a name="initinstance-member-function"></a>InitInstance, fonction membre

Le système d’exploitation Windows vous permet d’exécuter plus d’une copie, ou «instance», de la même application. `WinMain`appelle [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) chaque fois qu’une nouvelle instance de l’application commence.

La `InitInstance` mise en œuvre standard créée par le MFC Application Wizard effectue les tâches suivantes :

- Comme son action centrale, crée les modèles de documents qui à leur tour créer des documents, des vues et des fenêtres de cadre. Pour une description de ce processus, voir [Document Template Creation](../mfc/document-template-creation.md).

- Charge les options de fichiers standard à partir d’un fichier .ini ou du registre Windows, y compris les noms des fichiers les plus récemment utilisés.

- Enregistre un ou plusieurs modèles de documents.

- Pour une application MDI, crée une fenêtre de cadre principale.

- Traite la ligne de commande pour ouvrir un document spécifié sur la ligne de commande ou pour ouvrir un nouveau document vide.

Vous pouvez ajouter votre propre code d’initialisation ou modifier le code écrit par l’assistant.

> [!NOTE]
> Les applications MFC doivent être paraminées en tant qu’appartement à filet unique (STA). Si vous appelez [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) dans votre `InitInstance` remplacement, spécifiez COINIT_APARTMENTTHREADED (plutôt que COINIT_MULTITHREADED).

## <a name="see-also"></a>Voir aussi

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)
