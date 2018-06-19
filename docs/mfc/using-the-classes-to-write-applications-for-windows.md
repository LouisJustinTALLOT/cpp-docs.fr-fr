---
title: Utilisation des Classes pour écrire des Applications pour Windows | Documents Microsoft
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
ms.openlocfilehash: fa126f2772e1672a1484453fdffdd487b6c45959
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386143"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Utilisation des classes pour l'écriture d'applications pour Windows
Dans leur ensemble, les classes de la bibliothèque Microsoft Foundation classes (MFC) constituent une « infrastructure d’application », sur lequel vous générez une application pour le système d’exploitation Windows. À un niveau très général, le framework définit la structure d’une application et fournit des implémentations d’interface utilisateur standard qui peuvent être placées sur le squelette. Votre travail en tant que programmeur est de dans le reste de la structure, qui sont des composants qui sont spécifiques à votre application. Vous pouvez gagner du temps à l’aide de l’Assistant Application MFC pour créer les fichiers pour une application de départ très complète. Vous utilisez les éditeurs de ressources Microsoft Visual C++ pour concevoir visuellement, de vos éléments d’interface utilisateur et commandes d’affichage de classes pour connecter ces éléments au code et la bibliothèque de classes pour implémenter votre logique d’application spécifiques.  
  
 Version 3.0 et versions ultérieure de l’infrastructure MFC prend en charge la programmation pour les plateformes Win32, y compris Microsoft Windows 95 et versions ultérieures et Windows NT versions 3.51 et ultérieures. Prise en charge de MFC Win32 inclut le multithreading. Utilisez la version 1.5*x* si vous avez besoin effectuer une programmation de 16 bits.  
  
 Cette famille d’articles présente une vue d’ensemble de l’infrastructure d’application. Il décrit également les principaux objets qui composent votre application et la façon dont ils sont créés. Parmi les sujets abordés dans les articles suivants sont les suivants :  
  
-   [Le framework](../mfc/framework-mfc.md).  
  
-   Répartition des tâches entre l’infrastructure et votre code, comme décrit dans [génération à partir du Framework](../mfc/building-on-the-framework.md).  
  
-   [La classe d’application](../mfc/cwinapp-the-application-class.md), qui encapsule les fonctionnalités de niveau application.  
  
-   Comment [modèles de document](../mfc/document-templates-and-the-document-view-creation-process.md) créer et gérer des documents et les vues associées et fenêtres frame.  
  
-   Classe [CWnd](../mfc/window-objects.md), la classe de base racine de toutes les fenêtres.  
  
-   [Objets graphiques](../mfc/graphic-objects.md), tels que des stylets et des pinceaux.  
  
 Incluent d’autres parties du framework :  
  
-   [Objets fenêtres : vue d’ensemble](../mfc/window-objects.md)  
  
-   [Mappage et la gestion des messages](../mfc/message-handling-and-mapping.md)  
  
-   [CObject, la classe de Base racine dans MFC](../mfc/using-cobject.md)  
  
-   [Architecture document/vue](../mfc/document-view-architecture.md)  
  
-   [Boîtes de dialogue](../mfc/dialog-boxes.md)  
  
-   [Contrôles](../mfc/controls-mfc.md)  
  
-   [Barres de contrôles](../mfc/control-bars.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [Gestion de la mémoire](../mfc/memory-management.md)  
  
     Outre ce qui vous donne un avantage de l’écriture d’applications pour le système d’exploitation Windows, MFC rend également beaucoup plus facile d’écrire des applications qui utilisent spécifiquement la liaison et incorporation de la technologie OLE. Vous pouvez rendre votre application OLE visual modification du conteneur, un serveur d’édition visuelle OLE ou les deux, et vous pouvez ajouter Automation afin que les autres applications peuvent utiliser des objets à partir de votre application ou même le lecteur à distance.  
  
-   [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
     Le kit de développement de contrôle OLE (CDK) est maintenant entièrement intégré à l’infrastructure. Famille de cet article fournit une vue d’ensemble du développement de contrôles ActiveX MFC. (Les contrôles ActiveX ont été anciennement appelés contrôles OLE.)  
  
-   [Programmation de base de données](../data/data-access-programming-mfc-atl.md)  
  
     MFC fournit également deux ensembles de classes de base de données qui simplifient l’accès aux données de l’écriture applications. À l’aide des classes de base de données ODBC, vous pouvez vous connecter aux bases de données via un pilote de base de données ODBC (Open Connectivity), sélectionner des enregistrements à partir des tables et afficher des informations sur l’enregistrements dans un formulaire à l’écran. Utilisez les classes d’objet DAO (Data Access), vous pouvez travailler avec les bases de données via le moteur de base de données Microsoft Jet ou des sources de données de (non Jet) externes, y compris les sources de données ODBC.  
  
     En outre, MFC est entièrement activé pour l’écriture d’applications qui utilisent Unicode et jeux de caractères multioctets (MBCS), les jeux de caractères de spécifiquement codés sur deux octets (DBCS).  
  
 Pour obtenir un guide général à la documentation de MFC, consultez [Rubriques MFC générales](../mfc/general-mfc-topics.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)

