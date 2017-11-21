---
title: Assistant Application MFC | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.overview
dev_langs: C++
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0fac78eddcdf36ecc295841019f9e3f05e537802
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-application-wizard"></a>Assistant Application MFC
L’Assistant Application MFC génère une application qui, lors de la compilation, implémente les fonctionnalités de base d’une application exécutable (.exe) de Windows. L’application de démarrage MFC inclut des fichiers sources (.cpp) C++, fichiers de ressources (.rc), fichiers d’en-tête (.h) et un fichier projet (.vcxproj). Le code généré dans ces fichiers de démarrage est basé sur MFC.  
  
> [!NOTE]
>  Selon les options que vous sélectionnez, l’Assistant crée des fichiers supplémentaires dans votre projet. Par exemple, si vous sélectionnez **contextuelle** sur la [fonctionnalités avancées](../../mfc/reference/advanced-features-mfc-application-wizard.md) page, l’Assistant crée les fichiers qui sont nécessaires pour compiler les fichiers d’aide du projet. Pour plus d’informations sur les fichiers créés par l’Assistant, consultez [Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)et consultez le fichier Readme.txt dans le projet.  
  
## <a name="overview"></a>Vue d'ensemble  
 Cette page de l’Assistant décrit les paramètres de l’application pour l’application MFC que vous créez. Par défaut, l’Assistant crée un projet de comme suit :  
  
-   [Type d’application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md)  
  
    -   Le projet est créé avec la prise en charge avec onglet interface multidocument (MDI). Pour plus d’informations, consultez [SDI et MDI](../../mfc/sdi-and-mdi.md).  
  
    -   Le projet utilise le [Architecture Document/vue](../../mfc/document-view-architecture.md).  
  
    -   Le projet utilise des bibliothèques Unicode.  
  
    -   Le projet est créé à l’aide du style de projet Visual Studio et permet la commutation de style visuel.  
  
    -   Le projet utilise les MFC dans une DLL partagée. Pour plus d’informations, consultez [DLL dans Visual C++](../../build/dlls-in-visual-cpp.md).  
  
-   [Prise en charge des documents composés, Assistant Application MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)  
  
    -   Le projet n’assure aucune prise en charge des documents composés.  
  
-   [Chaînes modèles de document, Assistant Application MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)  
  
    -   Le projet utilise le nom du projet pour les chaînes de modèle de document par défaut.  
  
-   [Prise en charge des bases de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md)  
  
    -   Le projet ne fournit aucune prise en charge pour les bases de données.  
  
-   [Fonctionnalités de l’interface utilisateur, Assistant Application MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)  
  
    -   Le projet implémente Windows standard comme un menu système, une barre d’état, agrandir et réduire des zones, des fonctionnalités de l’interface utilisateur une **sur** zone, une barre de menus standard d’ancrage de barre d’outils et des frames enfants.  
  
-   [Fonctionnalités avancées, Assistant Application MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)  
  
    -   Le projet prend en charge l’impression et Aperçu avant impression.  
  
    -   Le projet prend en charge les contrôles ActiveX. Pour plus d’informations, consultez [séquence des opérations pour la création de contrôles ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).  
  
    -   Le projet n’assure aucune prise en charge pour [Automation](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md), ou Active Accessibility.  
  
    -   Le projet prend en charge une **Explorer** volet d’ancrage, une **sortie** volet d’ancrage et un **propriétés** volet d’ancrage.  
  
-   [Classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)  
  
    -   Classe d’affichage du projet est dérivée de la [classe CView](../../mfc/reference/cview-class.md).  
  
    -   Classe d’application du projet est dérivée de la [CWinAppEx classe](../../mfc/reference/cwinappex-class.md).  
  
    -   Classe de document du projet est dérivée de la [CDocument (classe)](../../mfc/reference/cdocument-class.md).  
  
    -   Classe de frame principal du projet est dérivée de la [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).  
  
    -   Classe de frame enfant du projet est dérivée de la [classe CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md).  
  
 Pour modifier ces paramètres par défaut, cliquez sur le titre de l’onglet approprié dans la colonne de gauche de l’Assistant et apporter les modifications sur la page qui s’affiche.  
  
 Après avoir créé un projet d’application MFC, vous pouvez ajouter des objets ou des contrôles à votre projet à l’aide de Visual C++ [Assistants de code](../../ide/adding-functionality-with-code-wizards-cpp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une Application MFC](../../mfc/reference/creating-an-mfc-application.md)   
 [Applications de bureau MFC](../../mfc/mfc-desktop-applications.md)   
 [Utilisation des classes pour l’écriture d’applications pour Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
