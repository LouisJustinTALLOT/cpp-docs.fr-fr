---
description: 'En savoir plus sur : Assistant Application MFC'
title: Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 645f0e1ed3f1f35c109d524a8c63fa36231bc61a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219211"
---
# <a name="mfc-application-wizard"></a>Assistant Application MFC

L’Assistant Application MFC génère une application qui, une fois compilée, implémente les fonctionnalités de base d’une application exécutable (. exe) Windows. L’application de démarrage MFC comprend des fichiers sources C++ (. cpp), des fichiers de ressources (. RC), des fichiers d’en-tête (. h) et un fichier projet (. vcxproj). Le code généré dans ces fichiers de démarrage est basé sur MFC.

> [!NOTE]
> En fonction des options que vous sélectionnez, l’Assistant crée des fichiers supplémentaires dans votre projet. Par exemple, si vous sélectionnez l' **aide** contextuelle sur la page [fonctionnalités avancées](../../mfc/reference/advanced-features-mfc-application-wizard.md) , l’Assistant crée les fichiers nécessaires à la compilation des fichiers d’aide du projet. Pour plus d’informations sur les fichiers créés par l’Assistant, consultez [types de fichiers créés pour les projets Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md)et consultez le fichier Readme.txt dans le projet.

## <a name="overview"></a>Vue d’ensemble

Cette page de l’Assistant décrit les paramètres d’application actuels pour l’application MFC que vous créez. Par défaut, l’Assistant crée un projet comme suit :

- [Type d’application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

  - Le projet est créé avec la prise en charge de l’interface MDI (multiple-document interface) avec onglet. Pour plus d’informations, consultez [SDI et MDI](../../mfc/sdi-and-mdi.md).

  - Le projet utilise l' [architecture document/vue](../../mfc/document-view-architecture.md).

  - Le projet utilise des bibliothèques Unicode.

  - Le projet est créé à l’aide du style de projet Visual Studio et active le basculement de style visuel.

  - Le projet utilise MFC dans une DLL partagée. Pour plus d’informations, consultez [créer des dll C/C++ dans Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Prise en charge des documents composés, Assistant Application MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - Le projet ne prend pas en charge les documents composés.

- [Chaînes de modèle de document, Assistant Application MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - Le projet utilise le nom du projet pour les chaînes du modèle de document par défaut.

- [Prise en charge des bases de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

  - Le projet ne prend pas en charge les bases de données.

- [Fonctionnalités de l’interface utilisateur, Assistant Application MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - Le projet implémente des fonctionnalités d’interface utilisateur Windows standard, telles qu’un menu système, une barre d’État, des zones d’agrandissement et de réduction, une boîte **de dialogue à propos** de, une barre de menus et une barre d’outils d’ancrage standard, ainsi que des cadres enfants.

- [Fonctionnalités avancées, Assistant Application MFC](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - Le projet prend en charge l’impression et l’aperçu avant impression.

  - Le projet prend en charge les contrôles ActiveX. Pour plus d’informations, consultez [séquence des opérations pour la création de contrôles ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

  - Le projet ne prend pas en charge l' [automatisation](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md)ou Active Accessibility.

  - Le projet prend en charge un volet d’ancrage de l' **Explorateur** , un volet d’ancrage de **sortie** et un volet d’ancrage des **Propriétés** .

- [Classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - La classe d’affichage du projet est dérivée de la [classe CView](../../mfc/reference/cview-class.md).

  - La classe d’application du projet est dérivée de la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md).

  - La classe de document du projet est dérivée de la [classe CDocument](../../mfc/reference/cdocument-class.md).

  - La classe de frame principale du projet est dérivée de la [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).

  - La classe de Frame enfant du projet est dérivée de la [classe CMDIChildWndEx,](../../mfc/reference/cmdichildwndex-class.md).

Pour modifier ces paramètres par défaut, cliquez sur le titre de l’onglet approprié dans la colonne de gauche de l’Assistant et apportez les modifications souhaitées dans la page qui s’affiche.

Après avoir créé un projet d’application MFC, vous pouvez ajouter des objets ou des contrôles à votre projet à l’aide de Visual C++ [assistants code](../../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="see-also"></a>Voir aussi

[Création d’une application MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[Applications de bureau MFC](../../mfc/mfc-desktop-applications.md)<br/>
[Utilisation des classes pour écrire des applications pour Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
