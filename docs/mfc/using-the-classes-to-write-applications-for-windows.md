---
title: Utilisation des Classes pour écrire des Applications pour Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c60cf5d6f61f16aac18524e8b6e75638ec13d27e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433333"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Utilisation des classes pour l'écriture d'applications pour Windows

Prises ensemble, les classes dans la bibliothèque Microsoft Foundation classes (MFC) constituent une « infrastructure d’application », sur lequel vous créez une application pour le système d’exploitation Windows. À un niveau très général, le framework définit la structure d’une application et fournit des implémentations d’interface utilisateur standard qui peuvent être placées sur le squelette. Votre travail en tant que programmeur consiste à remplir le reste de la structure, qui sont des composants qui sont spécifiques à votre application. Vous pouvez obtenir un point de départ à l’aide de l’Assistant Application MFC pour créer les fichiers pour une application de départ très complète. Les éditeurs de ressources de Microsoft Visual C++ pour concevoir vos éléments d’interface utilisateur visuellement, commandes d’affichage de classes pour connecter ces éléments au code et la bibliothèque de classes vous permet d’implémenter votre logique spécifique à l’application.

Version 3.0 et versions ultérieure de l’infrastructure MFC prend en charge la programmation pour les plateformes Win32, y compris Microsoft Windows 95 et versions ultérieures et Windows NT versions 3.51 et ultérieures. Prise en charge de MFC Win32 inclut le multithreading. Utilisez la version 1.5*x* si vous avez besoin effectuer la programmation de 16 bits.

Cette série d’articles présente une vue d’ensemble de l’infrastructure d’application. Il explore également les objets principaux qui composent votre application et comment ils sont créés. Parmi les sujets abordés dans ces articles sont les suivantes :

- [Le framework](../mfc/framework-mfc.md).

- Répartition des tâches entre l’infrastructure et votre code, comme décrit dans [création sur Framework](../mfc/building-on-the-framework.md).

- [La classe application](../mfc/cwinapp-the-application-class.md), qui encapsule les fonctionnalités de niveau application.

- Comment [modèles de document](../mfc/document-templates-and-the-document-view-creation-process.md) créer et gérer des documents et leurs vues associées et fenêtres frame.

- Classe [CWnd](../mfc/window-objects.md), la classe de base racine de toutes les fenêtres.

- [Objets graphiques](../mfc/graphic-objects.md), tels que des stylets et des pinceaux.

Autres parties de l’infrastructure sont les suivantes :

- [Objets de fenêtre : vue d’ensemble](../mfc/window-objects.md)

- [Mappage et gestion des messages](../mfc/message-handling-and-mapping.md)

- [CObject, la classe de Base racine dans MFC](../mfc/using-cobject.md)

- [Architecture document/vue](../mfc/document-view-architecture.md)

- [Boîtes de dialogue](../mfc/dialog-boxes.md)

- [Contrôles](../mfc/controls-mfc.md)

- [Barres de contrôles](../mfc/control-bars.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Gestion de la mémoire](../mfc/memory-management.md)

     Outre ce qui vous donne un avantage à écrire des applications pour le système d’exploitation Windows, MFC rend également beaucoup plus facile d’écrire des applications qui utilisent spécifiquement de liaison et incorporation technologie OLE. Vous pouvez rendre votre application OLE visual modification du conteneur, un serveur d’édition visuelle OLE ou les deux, et vous pouvez ajouter Automation afin que les autres applications peuvent utiliser des objets à partir de votre application ou même le lecteur à distance.

- [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

     Le kit de développement de contrôle OLE (CDK) est maintenant entièrement intégré à l’infrastructure. Famille de cet article fournit une vue d’ensemble du développement de contrôles ActiveX avec MFC. (Les contrôles ActiveX ont été anciennement contrôles OLE.)

- [Programmation de base de données](../data/data-access-programming-mfc-atl.md)

     MFC fournit également deux ensembles de classes de base de données qui simplifient l’écriture d’accès aux données des applications. À l’aide des classes de base de données ODBC, vous pouvez vous connecter aux bases de données via un pilote Open Database Connectivity (ODBC), sélectionner des enregistrements de tables et afficher les informations de l’enregistrement dans un formulaire à l’écran. En utilisant les classes d’objet DAO (Data Access), vous pouvez manipuler les bases de données via le moteur de base de données Microsoft Jet ou les sources de données de (non Jet) externes, y compris les sources de données ODBC.

     En outre, MFC est entièrement activé pour écrire des applications qui utilisent Unicode et jeux de caractères multioctets (MBCS), spécifiquement double jeux de caractères (DBCS).

Pour obtenir une aide générale à la documentation de MFC, consultez [Rubriques MFC générales](../mfc/general-mfc-topics.md).

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)

