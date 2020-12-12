---
description: 'En savoir plus sur : utilisation des classes pour écrire des applications pour Windows'
title: Utilisation des classes pour l'écriture d'applications pour Windows
ms.date: 11/04/2016
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
ms.openlocfilehash: b94155b565872b614efa291699cecbaf4770fdaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322710"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Utilisation des classes pour l'écriture d'applications pour Windows

Pris ensemble, les classes de la bibliothèque MFC (Microsoft Foundation Class) constituent une « infrastructure d’application », sur laquelle vous générez une application pour le système d’exploitation Windows. À un niveau très général, le Framework définit la structure d’une application et fournit des implémentations standard de l’interface utilisateur qui peuvent être placées sur la structure. Votre travail en tant que programmeur est de remplir le reste du squelette, qui sont les éléments spécifiques à votre application. Vous pouvez commencer à utiliser l’Assistant Application MFC pour créer les fichiers d’une application de démarrage très approfondie. Vous utilisez les Microsoft Visual C++ éditeurs de ressources pour concevoir visuellement vos éléments d’interface utilisateur, Affichage de classes des commandes pour connecter ces éléments au code, et la bibliothèque de classes pour implémenter la logique spécifique à votre application.

La version 3,0 et les versions ultérieures de l’infrastructure MFC prennent en charge la programmation pour les plateformes Win32, notamment Microsoft Windows 95 et versions ultérieures, et Windows NT versions 3,51 et ultérieures. La prise en charge de MFC Win32 comprend le multithread. Utilisez la version 1,5 *x* si vous devez programmer 16 bits.

Cette famille d’articles présente une vue d’ensemble générale de l’infrastructure d’application. Il explore également les principaux objets qui composent votre application et la façon dont ils sont créés. Parmi les sujets abordés dans ces articles, citons les suivantes :

- [Framework](../mfc/framework-mfc.md).

- Division du travail entre l’infrastructure et votre code, comme décrit dans [génération sur le Framework](../mfc/building-on-the-framework.md).

- [La classe d’application](../mfc/cwinapp-the-application-class.md), qui encapsule les fonctionnalités au niveau de l’application.

- Comment les [modèles de document](../mfc/document-templates-and-the-document-view-creation-process.md) créent et gèrent des documents et leurs vues et fenêtres Frame associées.

- Classe [CWnd](../mfc/window-objects.md), la classe de base racine de toutes les fenêtres.

- [Objets graphiques](../mfc/graphic-objects.md), tels que les stylets et les pinceaux.

Les autres parties de l’infrastructure sont les suivantes :

- [Objets de fenêtre : vue d’ensemble](../mfc/window-objects.md)

- [Gestion et mappage des messages](../mfc/message-handling-and-mapping.md)

- [CObject, la classe de base racine dans MFC](../mfc/using-cobject.md)

- [Architecture document/vue](../mfc/document-view-architecture.md)

- [Boîtes de dialogue](../mfc/dialog-boxes.md)

- [Contrôles](../mfc/controls-mfc.md)

- [Barres de contrôles](../mfc/control-bars.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Gestion de la mémoire](../mfc/memory-management.md)

   En plus de vous donner un avantage à l’écriture d’applications pour le système d’exploitation Windows, MFC facilite également l’écriture d’applications qui utilisent spécifiquement la technologie de liaison et d’incorporation OLE. Vous pouvez faire de votre application un conteneur d’édition visuelle OLE, un serveur d’édition visuelle OLE, ou les deux, et vous pouvez ajouter l’automatisation afin que d’autres applications puissent utiliser des objets de votre application ou même les piloter à distance.

- [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

   Le kit de développement de contrôle OLE (CDK) est maintenant entièrement intégré à l’infrastructure. Cette famille d’articles fournit une vue d’ensemble du développement de contrôles ActiveX avec MFC. (Les contrôles ActiveX étaient auparavant appelés contrôles OLE.)

- [Programmation de base de données](../data/data-access-programming-mfc-atl.md)

   MFC fournit également deux ensembles de classes de base de données qui simplifient l’écriture d’applications d’accès aux données. À l’aide des classes de base de données ODBC, vous pouvez vous connecter aux bases de données via un pilote Open Database Connectivity (ODBC), sélectionner des enregistrements dans des tables et afficher les informations sur les enregistrements dans un formulaire à l’écran. À l’aide des classes d’objets d’accès aux données (DAO), vous pouvez travailler avec des bases de données à l’aide du moteur de base de données Microsoft Jet ou de sources de données externes (non-jet), y compris les sources de données ODBC.

   En outre, MFC est entièrement activé pour l’écriture d’applications utilisant Unicode et les jeux de caractères multioctets (MBCS), en particulier les jeux de caractères codés sur deux octets (DBCS).

Pour obtenir un guide général de la documentation MFC, consultez les [rubriques générales sur MFC](../mfc/general-mfc-topics.md).

## <a name="see-also"></a>Voir aussi

[Rubriques générales sur MFC](../mfc/general-mfc-topics.md)
