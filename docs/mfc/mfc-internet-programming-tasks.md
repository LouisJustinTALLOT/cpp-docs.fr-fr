---
title: Tâches de programmation Internet MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df7efbc8d29b2e36c6911255389cc270e7bf5e37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347244"
---
# <a name="mfc-internet-programming-tasks"></a>Tâches de programmation Internet MFC
Cette section contient des procédures détaillées pour ajouter la prise en charge d'Internet dans vos applications. Les rubriques suivantes expliquent comment utiliser les classes MFC dans vos applications existantes avec Internet, et comment ajouter la prise en charge des documents actifs vers votre composant COM existant. Vous souhaitez créer un document avec boursiers, équipe de football de Pittsburgh, et la dernière température en Antarctique Microsoft fournit un certain nombre de technologies pour vous aider à le faire sur Internet.  
  
 Les technologies Active incluent des contrôles ActiveX (anciennement contrôles OLE) et des documents Active, WinInet pour récupérer et enregistrer facilement des fichiers sur Internet, et des monikers asynchrones pour un téléchargement de données performant. Visual C++ propose des assistants pour vous faire découvrir une application de départ. Pour obtenir une présentation de ces technologies, consultez [notions de programmation Internet MFC](../mfc/mfc-internet-programming-basics.md) et [MFC COM](../mfc/mfc-com.md).  
  
 Toujours voulu FTP d’un fichier, mais ne l’avez pas appris WinSock et programmation des classes WinInet de protocoles réseau encapsulent ces protocoles, vous offrant un ensemble de fonctions que vous pouvez utiliser pour écrire une application cliente sur Internet pour télécharger les fichiers simple à l’aide de HTTP, FTP et gopher. Vous pouvez utiliser WinInet pour rechercher des répertoires sur votre disque dur ou partout dans le monde. Vous pouvez de façon transparente collecter des données de différents types, et les présenter aux utilisateurs dans une interface intégrée.  
  
 Avez-vous de grandes quantités de données à télécharger asynchrone monikers fournissent une solution COM (Component Object Model) pour le rendu progressif des objets de grande taille. WinInet peut également être utilisé de manière asynchrone.  
  
 Le tableau suivant décrit quelques unes des opérations réalisables avec ces technologies.  
  
|Vous avez|Vous souhaitez|Vous devez|  
|--------------|-----------------|----------------|  
|Un serveur web.|Faire le suivi des connexions et obtenir des informations sur les demandes d'URL.|Écrire un filtre, demander des notifications en cas d'ouverture de session et de mappage d'URL.|  
|Un navigateur Web.|Fournir un contenu dynamique.|Créer des contrôles ActiveX et des documents Active.|  
|Une application basée sur les documents.|Ajouter la prise en charge d'un fichier sur un serveur FTP.|Utiliser WinInet ou des monikers asynchrones.|  
  
 Consultez les rubriques suivantes pour savoir comment démarrer :  
  
-   [Choix en matière de conception d’applications](../mfc/application-design-choices.md)  
  
-   [Écriture d’applications MFC](../mfc/writing-mfc-applications.md)  
  
-   [Contrôles ActiveX sur Internet](../mfc/activex-controls-on-the-internet.md)  
  
-   [Mise à niveau d’un contrôle ActiveX](../mfc/upgrading-an-existing-activex-control.md)  
  
-   [Documents actifs sur Internet](../mfc/active-documents-on-the-internet.md)  
  
-   [Monikers asynchrones sur Internet](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Test des applications Internet](../mfc/testing-internet-applications.md)  
  
-   [Sécurité Internet](../mfc/internet-security-cpp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Base de programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)   
 [Informations Internet par tâche](../mfc/internet-information-by-task.md)

