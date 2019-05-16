---
title: Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: e97c7a29dd56a69fad99e85c206ca2104fa71798
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708199"
---
# <a name="mfc-application-wizard"></a>Assistant Application MFC

L’Assistant Application MFC génère une application qui, lors de la compilation, implémente les fonctionnalités de base d’une application exécutable (.exe) de Windows. L’application de démarrage MFC inclut des fichiers sources (.cpp) C++, les fichiers de ressources (.rc), les fichiers d’en-tête (.h) et un fichier projet (.vcxproj). Le code généré dans ces fichiers de démarrage est basé sur la bibliothèque MFC.

> [!NOTE]
>  Selon les options que vous sélectionnez, l’Assistant crée des fichiers supplémentaires dans votre projet. Par exemple, si vous sélectionnez **aide contextuelle** sur le [fonctionnalités avancées](../../mfc/reference/advanced-features-mfc-application-wizard.md) page, l’Assistant crée les fichiers qui sont nécessaires pour compiler les fichiers d’aide du projet. Pour plus d’informations sur les fichiers créés par l’Assistant, consultez [Types de fichiers créés pour Visual Studio C++ projets](../../build/reference/file-types-created-for-visual-cpp-projects.md)et consultez le fichier Readme.txt dans le projet.

## <a name="overview"></a>Vue d'ensemble

Cette page de l’Assistant décrit les paramètres de l’application pour l’application MFC que vous créez. Par défaut, l’Assistant crée un projet comme suit :

- [Type d’application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

   - Le projet est créé avec la prise en charge avec onglet interface multidocument (MDI). Pour plus d’informations, consultez [SDI et MDI](../../mfc/sdi-and-mdi.md).

   - Le projet utilise le [Architecture Document/vue](../../mfc/document-view-architecture.md).

   - Le projet utilise des bibliothèques Unicode.

   - Le projet est créé en utilisant le style de projet Visual Studio et permet la commutation de style visuel.

   - Le projet utilise les MFC dans une DLL partagée. Pour plus d’informations, consultez [créer C /C++ DLL dans Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Prise en charge des documents composés, Assistant Application MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

   - Le projet ne fournit aucune prise en charge des documents composés.

- [Chaînes modèles de document, Assistant Application MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

   - Le projet utilise le nom du projet pour les chaînes de modèle de document par défaut.

- [Prise en charge des bases de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

   - Le projet ne fournit aucune prise en charge pour les bases de données.

- [Fonctionnalités de l’interface utilisateur, Assistant Application MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

   - Le projet implémente Windows standard, les fonctionnalités d’interface utilisateur comme un menu système, une barre d’état, optimiser et réduire des zones, un **sur** boîte, une barre de menus standard d’ancrage de barre d’outils et des frames enfants.

- [Fonctionnalités avancées, Assistant Application MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)

   - Le projet prend en charge l’impression et Aperçu avant impression.

   - Le projet prend en charge les contrôles ActiveX. Pour plus d’informations, consultez [séquence des opérations pour la création de contrôles ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

   - Le projet ne fournit aucune prise en charge pour [Automation](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md), ou Active Accessibility.

   - Le projet prend en charge un **Explorer** volet d’ancrage, un **sortie** volet d’ancrage et un **propriétés** volet d’ancrage.

- [Classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)

   - Classe de vue du projet est dérivée de la [classe CView](../../mfc/reference/cview-class.md).

   - Classe d’application du projet est dérivée de la [CWinAppEx, classe](../../mfc/reference/cwinappex-class.md).

   - Classe de document du projet est dérivée de la [CDocument (classe)](../../mfc/reference/cdocument-class.md).

   - Classe de frame principal du projet est dérivée de la [CMDIFrameWndEx, classe](../../mfc/reference/cmdiframewndex-class.md).

   - Classe de frame enfant du projet est dérivée de la [CMDIChildWndEx, classe](../../mfc/reference/cmdichildwndex-class.md).

Pour modifier ces paramètres par défaut, cliquez sur le titre de l’onglet approprié dans la colonne de gauche de l’Assistant et apporter les modifications sur la page qui s’affiche.

Après avoir créé un projet d’application MFC, vous pouvez ajouter des objets ou des contrôles à votre projet à l’aide de Visual C++ [Assistants de code](../../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="see-also"></a>Voir aussi

[Création d’une application MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[MFC, applications de bureau](../../mfc/mfc-desktop-applications.md)<br/>
[Utilisation des classes pour l’écriture d’applications pour Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
