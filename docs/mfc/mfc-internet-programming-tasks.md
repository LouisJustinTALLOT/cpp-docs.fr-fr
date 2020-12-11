---
description: 'En savoir plus sur : tâches de programmation Internet MFC'
title: Tâches de programmation Internet MFC
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
ms.openlocfilehash: 26823dbd85222998ebf20947ac2af30a6b11e987
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159932"
---
# <a name="mfc-internet-programming-tasks"></a>Tâches de programmation Internet MFC

Cette section contient des procédures détaillées pour ajouter la prise en charge d'Internet dans vos applications. Les rubriques suivantes expliquent comment utiliser les classes MFC dans vos applications existantes avec Internet, et comment ajouter la prise en charge des documents actifs vers votre composant COM existant. Souhaitez-vous créer un document avec des cotations boursières à la minute, des scores de football Pittsburgh et la dernière température en Antarctique Microsoft fournit un certain nombre de technologies pour vous aider à le faire sur Internet.

Les technologies Active incluent des contrôles ActiveX (anciennement contrôles OLE) et des documents Active, WinInet pour récupérer et enregistrer facilement des fichiers sur Internet, et des monikers asynchrones pour un téléchargement de données performant. Visual C++ propose des assistants pour vous faire découvrir une application de départ. Pour obtenir une présentation de ces technologies, consultez concepts de base de la [programmation Internet MFC](mfc-internet-programming-basics.md) et [MFC com](mfc-com.md).

Avez-vous toujours voulu transférer un fichier via FTP, mais vous n’avez pas appris les classes WinInet WinSock et Network Programming Protocols pour encapsuler ces protocoles, en vous fournissant un ensemble simple de fonctions que vous pouvez utiliser pour écrire une application cliente sur Internet afin de télécharger des fichiers à l’aide de HTTP, FTP et Gopher. Vous pouvez utiliser WinInet pour rechercher des répertoires sur votre disque dur ou partout dans le monde. Vous pouvez de façon transparente collecter des données de différents types, et les présenter aux utilisateurs dans une interface intégrée.

Disposez-vous de grandes quantités de données pour télécharger des monikers asynchrones, fournissez une solution COM (Component Object Model) pour le rendu progressif des objets volumineux. WinInet peut également être utilisé de manière asynchrone.

Le tableau suivant décrit quelques unes des opérations réalisables avec ces technologies.

|Vous avez|Vous souhaitez|Vous devez|
|--------------|-----------------|----------------|
|Un serveur web.|Faire le suivi des connexions et obtenir des informations sur les demandes d'URL.|Écrire un filtre, demander des notifications en cas d'ouverture de session et de mappage d'URL.|
|Un navigateur Web.|Fournir un contenu dynamique.|Créer des contrôles ActiveX et des documents Active.|
|Une application basée sur les documents.|Ajouter la prise en charge d'un fichier sur un serveur FTP.|Utiliser WinInet ou des monikers asynchrones.|

Consultez les rubriques suivantes pour savoir comment démarrer :

- [Choix de conception d’application](application-design-choices.md)

- [Écriture d’applications MFC](writing-mfc-applications.md)

- [Contrôles ActiveX sur Internet](activex-controls-on-the-internet.md)

- [Mise à niveau d’un contrôle ActiveX existant](upgrading-an-existing-activex-control.md)

- [Monikers asynchrones sur Internet](asynchronous-monikers-on-the-internet.md)

- [Test des applications Internet](testing-internet-applications.md)

- [Sécurité Internet](internet-security-cpp.md)

## <a name="see-also"></a>Voir aussi

[Concepts de base de la programmation Internet MFC](mfc-internet-programming-basics.md)<br/>
[Informations Internet par tâche](internet-information-by-task.md)
