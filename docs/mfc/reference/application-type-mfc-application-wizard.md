---
description: 'En savoir plus sur : type d’application, Assistant Application MFC'
title: Type d'application, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.apptype
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
ms.openlocfilehash: 178e9c1319b17e356273fc3e59d2133c8d4aa54c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322783"
---
# <a name="application-type-mfc-application-wizard"></a>Type d'application, Assistant Application MFC

Utilisez cette page de l ['Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md) pour concevoir et ajouter des fonctionnalités de base à une nouvelle application MFC.

- **Type d’application**

  Spécifie le type de prise en charge de document que vous souhaitez créer dans votre application. Le type d’application que vous sélectionnez détermine les options d’interface utilisateur disponibles pour votre application. Pour plus d’informations [, consultez fonctionnalités de l’interface utilisateur, Assistant Application MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md) .

   Pour plus d’informations sur les types de documents, consultez :

  - [SDI et MDI](../../mfc/sdi-and-mdi.md)

  - [Fenêtres Frame](../../mfc/frame-windows.md)

  - [Classes de fenêtre frame](../../mfc/frame-window-classes.md)

  - [Documents, vues et le Framework](../../mfc/documents-views-and-the-framework.md)

  - [Boîtes de dialogue](../../mfc/dialog-boxes.md)

  |Option|Description|
  |------------|-----------------|
  |**Document individuel**|Crée une architecture SDI (single document interface) pour votre application, où une classe d’affichage est basée sur la [classe CView](../../mfc/reference/cview-class.md). Vous pouvez modifier la classe de base de la vue dans la page [classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) de l’Assistant. Pour créer une application basée sur des formulaires, par exemple, utilisez la [classe CFormView](../../mfc/reference/cformview-class.md) pour la classe d’affichage.<br /><br /> Dans ce type d’application, la fenêtre frame du document ne peut contenir qu’un seul document.|
  |**Documents multiples**|Crée une architecture d’interface multidocument (MDI, multiple document interface) pour votre application, où une classe d’affichage est basée sur `CView` . Vous pouvez modifier la classe de base de la vue dans la page **classes générées** de l’Assistant. Pour créer une application basée sur des formulaires, par exemple, utilisez `CFormView` pour la classe d’affichage.<br /><br /> Dans ce type d’application, la fenêtre frame du document peut contenir plusieurs fenêtres enfants.|
  |**Documents avec onglet**|Place chaque document dans un onglet séparé.|
  |**Basée sur une boîte de dialogue**|Crée une architecture basée sur des boîtes de dialogue pour votre application sur laquelle est basée une classe de boîte de dialogue `CDialog` . (Pour créer une boîte de dialogue HTML, cochez la case utiliser la boîte de **dialogue HTML**.)|
  |**Utiliser la boîte de dialogue HTML**|Pour les applications de boîte de dialogue uniquement. Dérive la classe de boîte de dialogue de la [classe CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) au lieu de la [classe CDialog](../../mfc/reference/cdialog-class.md). Si vous activez cette case à cocher, `CDHtmlDialog` est listé dans la zone **classe de base** de la page [classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) de l’Assistant.<br /><br /> Une `CDHtmlDialog` boîte de dialogue dérivée de affiche des boîtes de dialogue HTML, échange des données avec des contrôles HTML et gère les événements html.|
  |**Plusieurs documents de niveau supérieur**|Crée une architecture de niveau supérieur pour votre application, où une classe d’affichage est basée sur `CView` .<br /><br /> Dans ce type d’application, lorsqu’un utilisateur clique sur **nouveau** (ou **nouveau Frame**) dans le menu **fichier** , l’application crée une fenêtre dont le parent est implicitement le bureau. Le nouveau frame de document s’affiche dans la barre des tâches et n’est pas limité à la zone cliente de la fenêtre d’application.|

- **Prise en charge de l’architecture document/vue**

  Spécifie s’il faut inclure l’architecture document/vue dans votre application à l’aide de la [classe CDocument](../../mfc/reference/cdocument-class.md) et de la [classe CView](../../mfc/reference/cview-class.md) (par défaut). Désactivez cette case à cocher si vous portez une application non-MFC ou si vous souhaitez réduire la taille de votre exécutable compilé. Par défaut, une application sans architecture document/vue est dérivée de la [classe CWinApp](../../mfc/reference/cwinapp-class.md)et n’inclut pas la prise en charge MFC pour l’ouverture d’un document à partir d’un fichier sur disque.

- **Langue des ressources**

  Définit la langue de vos ressources. La liste affiche les langues disponibles sur votre système, telles qu’elles sont installées par Visual Studio. Si vous souhaitez sélectionner une langue autre que la langue de votre système, le dossier de modèles approprié pour cette langue doit déjà être installé.

  La langue que vous sélectionnez est reflétée dans l’option **chaînes localisées** de la page [chaînes du modèle de document, Assistant Application MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) de l’Assistant.

- **Utiliser des bibliothèques Unicode**

  Spécifie si la version Unicode ou non Unicode des bibliothèques MFC est utilisée.

- **Style du projet**

  Indique si votre application dispose d’une architecture MFC, de l’Explorateur de fichiers, de Visual Studio ou d’Office et d’un affichage standard. Pour plus d’informations, consultez [création d’un fichier Explorer-Style application MFC](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).

  |Option|Description|
  |------------|-----------------|
  |**MFC standard**|Fournit une architecture d’application MFC standard.|
  |**Explorateur de fichiers**|Implémente une application de type Explorateur de fichiers à l’aide d’une fenêtre fractionnée où le volet gauche est une [classe CTreeView](../../mfc/reference/ctreeview-class.md) et le volet droit est une [classe CListView](../../mfc/reference/clistview-class.md).|
  |**Visual Studio**|Implémente une application de type Visual Studio qui contient quatre volets ancrables **(affichage des fichiers**, **affichage de classes**, **Propriétés** et **sorties**) dérivés de la [classe CDockablePane](../../mfc/reference/cdockablepane-class.md) et une fenêtre frame principale dérivée de la [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md) (valeur par défaut).|
  |**Office**|Implémente une application de type Office qui contient un ruban dérivé de la [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md), une barre Outlook dérivée de la [classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md), une barre de légende dérivée de la [classe CMFCCaptionBar,](../../mfc/reference/cmfccaptionbar-class.md)et un frame principal dérivé de la [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).|

- **Style visuel et couleurs**

  Détermine le style visuel de l’application. Les options suivantes sont disponibles :

  - **Windows natif/par défaut**

  - **Office 2003**

  - **Visual Studio 2005**

  - **Office 2007 (thème Blue)**

  - **Office 2007 (thème noir)**

  - **Office 2007 (thème argent)**

  - **Office 2007 (thème Aqua)**

- **Activer le basculement de style visuel**

  Spécifie si l’utilisateur peut modifier le style visuel de l’application au moment de l’exécution, généralement en sélectionnant le style visuel approprié à partir d’un menu ou d’un ruban.

- **Utilisation des MFC**

  Spécifie comment créer un lien vers la bibliothèque MFC. Par défaut, les MFC sont liées en tant que DLL partagées.

  |Option|Description|
  |------------|-----------------|
  |**Utiliser MFC dans une DLL partagée**|Lie la bibliothèque MFC à une application en tant que DLL partagée. L’application effectue des appels à la bibliothèque MFC au moment de l’exécution. Cette option réduit les besoins en disque et en mémoire des applications qui se composent de plusieurs fichiers exécutables qui utilisent la bibliothèque MFC. Les applications Win32 et MFC peuvent appeler des fonctions dans votre DLL (par défaut)|
  |**Utiliser MFC dans une bibliothèque statique**|Lie une application à la bibliothèque MFC statique au moment de la génération.|

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Types de fichiers créés pour les projets Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md)
