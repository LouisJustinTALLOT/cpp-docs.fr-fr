---
title: Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 6949f136890e8274f225a49496b2eb1b8f78b6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351832"
---
# <a name="mfc-application-wizard"></a>Assistant Application MFC

L’assistant d’application MFC génère une application qui, une fois compilée, implémente les caractéristiques de base d’une application exécutable Windows (.exe). L’application de démarrage MFC comprend des fichiers de source (.cpp) de C, des fichiers de ressources (.rc), des fichiers d’en-tête (.h) et un fichier de projet (.vcxproj). Le code généré dans ces fichiers de démarrage est basé sur MFC.

> [!NOTE]
> Selon les options que vous sélectionnez, l’assistant crée des fichiers supplémentaires dans votre projet. Par exemple, si vous sélectionnez **de l’aide contextuelle** sur la page [Fonctionnalités Avancées,](../../mfc/reference/advanced-features-mfc-application-wizard.md) l’assistant crée les fichiers nécessaires à la compilation des fichiers d’aide du projet. Pour plus d’informations sur les fichiers que l’assistant crée, voir [les types de fichiers créés pour les projets Visual Studio C ,](../../build/reference/file-types-created-for-visual-cpp-projects.md)et voir le fichier Readme.txt dans le projet.

## <a name="overview"></a>Vue d’ensemble

Cette page d’assistant décrit les paramètres d’application actuels de l’application MFC que vous créez. Par défaut, l’assistant crée un projet comme suit :

- [Type d'application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md)

  - Le projet est créé avec le support de l’interface multi-documents (MDI) tabbed. Pour plus d’informations, voir [SDI et MDI](../../mfc/sdi-and-mdi.md).

  - Le projet utilise [l’architecture Document/View](../../mfc/document-view-architecture.md).

  - Le projet utilise les bibliothèques Unicode.

  - Le projet est créé en utilisant le style du projet Visual Studio et permet la commutation visuelle de style.

  - Le projet utilise MFC dans un DLL partagé. Pour plus d’informations, voir [Créer des DLL C/CMD dans Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Support de document composé, Assistant d’application MFC](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - Le projet ne fournit aucun soutien aux documents composés.

- [Chaînes de modèle de document, Assistant d’application MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - Le projet utilise le nom du projet pour les chaînes de modèles de documents par défaut.

- [Support de base de données, Assistant d’application MFC](../../mfc/reference/database-support-mfc-application-wizard.md)

  - Le projet ne fournit aucun support pour les bases de données.

- [Caractéristiques d’interface utilisateur, Assistant d’application MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - Le projet implémente des fonctionnalités standard d’interface utilisateur Windows telles qu’un menu système, une barre d’état, maximiser et minimiser les boîtes, une boîte **About,** une barre de menu standard et une barre d’outils d’amarrage, et des cadres pour enfants.

- [Caractéristiques avancées, MFC Application Wizard](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - Le projet prend en charge l’impression et l’impression.

  - Le projet prend en charge les contrôles ActiveX. Pour plus d’informations, voir [Séquence d’opérations pour créer des contrôles ActiveX](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

  - Le projet ne fournit aucun support pour [l’automatisation](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets,](../../mfc/windows-sockets-in-mfc.md)ou Active Accessibility.

  - Le projet prend en charge une vitre d’amarrage **Explorer,** une vitre d’amarrage **De sortie** et une vitre d’amarrage **Propriétés.**

- [Classes générées, MFC Application Wizard](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - La classe de vue du projet est dérivée de la [classe CView](../../mfc/reference/cview-class.md).

  - La classe de demande du projet est dérivée de la [classe CWinAppEx](../../mfc/reference/cwinappex-class.md).

  - La classe de documents du projet est dérivée de la [classe CDocument](../../mfc/reference/cdocument-class.md).

  - La classe de cadre principale du projet est dérivée de la [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).

  - La classe de cadre pour enfants du projet est dérivée de la [classe CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md).

Pour modifier ces paramètres par défaut, cliquez sur le titre de l’onglet approprié dans la colonne gauche de l’assistant et effectuez les modifications sur la page qui s’affiche.

Après avoir créé un projet d’application MFC, vous pouvez ajouter des objets ou des contrôles à votre projet à l’aide de [magiciens de code](../../ide/adding-functionality-with-code-wizards-cpp.md)Visual CMD .

## <a name="see-also"></a>Voir aussi

[Création d'une application MFC](../../mfc/reference/creating-an-mfc-application.md)<br/>
[MFC, applications de bureau](../../mfc/mfc-desktop-applications.md)<br/>
[Utilisation des classes pour l’écriture d’applications pour Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
