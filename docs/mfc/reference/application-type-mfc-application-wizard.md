---
title: Type d'application, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.apptype
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
ms.openlocfilehash: 285760f71e0dfad0a6ef6011d79e0f3f2ce6760d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642293"
---
# <a name="application-type-mfc-application-wizard"></a>Type d'application, Assistant Application MFC

Utilisez cette page de la [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md) pour concevoir et ajouter des fonctionnalités de base pour une application MFC.

- **Type d’application**

   Spécifie le type de prise en charge de document que vous souhaitez créer dans votre application. Le type d’application que vous sélectionnez détermine les options d’interface utilisateur qui sont disponibles pour votre application. Consultez [fonctionnalités d’Interface utilisateur, Assistant Application MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md) pour plus d’informations.

   Pour plus d’informations sur les types de documents, consultez :

   - [SDI et MDI](../../mfc/sdi-and-mdi.md)

   - [Fenêtres frame](../../mfc/frame-windows.md)

   - [Classes de fenêtre frame](../../mfc/frame-window-classes.md)

   - [Documents, vues et le Framework](../../mfc/documents-views-and-the-framework.md)

   - [Boîtes de dialogue](../../mfc/dialog-boxes.md)

   |Option|Description|
   |------------|-----------------|
   |**Seul document**|Crée une architecture d’interface (monodocument SDI) de document unique pour votre application, où une classe de vue est basée sur [classe CView](../../mfc/reference/cview-class.md). Vous pouvez modifier la classe de base pour l’affichage dans le [Classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de l’Assistant. Pour créer une application basée sur le formulaire, par exemple, utilisez [CFormView, classe](../../mfc/reference/cformview-class.md) pour la classe d’affichage.<br /><br /> Dans ce type d’application, fenêtre frame de document peut contenir qu’un seul document.|
   |**Plusieurs documents**|Crée une architecture pour votre application, où une classe de vue est basée sur l’interface (multidocument MDI) document `CView`. Vous pouvez modifier la classe de base pour l’affichage dans le **Classes générées** page de l’Assistant. Pour créer une application basée sur le formulaire, par exemple, utilisez `CFormView` pour la classe d’affichage.<br /><br /> Dans ce type d’application, fenêtre frame de document peut contenir plusieurs fenêtres enfants.|
   |**Documents avec onglet**|Place chaque document dans un onglet séparé.|
   |**Boîte de dialogue en fonction**|Crée une architecture basée sur la boîte de dialogue pour votre application où une classe de boîte de dialogue est basée sur `CDialog`. (Pour créer une boîte de dialogue HTML, activez la case à **boîte de dialogue utilisation HTML**.)|
   |**Utilisez la boîte de dialogue HTML**|Pour les applications boîte dialogue uniquement. Dérive de la classe de boîte de dialogue à partir de [CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md) au lieu de [classe CDialog](../../mfc/reference/cdialog-class.md). Si vous cochez cette case, `CDHtmlDialog` est répertorié dans le **classe de Base** zone le [Classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de l’Assistant.<br /><br /> Un `CDHtmlDialog`-boîte de dialogue dérivée affiche des boîtes de dialogue HTML, échange des données avec HTML, contrôle et gère les événements HTML.|
   |**Plusieurs documents de niveau supérieur**|Crée une architecture niveau supérieur pour votre application, où une classe de vue est basée sur `CView`.<br /><br /> Dans ce type d’application, lorsqu’un utilisateur clique **New** (ou **nouveau Frame**) sur le **fichier** menu, l’application crée une fenêtre dont le parent est implicitement le bureau. Le nouveau frame de document apparaît dans la barre des tâches et n’est pas limité à la zone cliente de la fenêtre d’application.|

- **Prise en charge de l’architecture de document/vue**

   Spécifie s’il faut inclure l’architecture document/vue dans votre application à l’aide de la [CDocument (classe)](../../mfc/reference/cdocument-class.md) et [classe CView](../../mfc/reference/cview-class.md) (valeur par défaut). Désactivez cette case à cocher si vous portez une application non-MFC ou si vous souhaitez réduire la taille de l’exécutable compilé. Par défaut, une application sans architecture document/vue est dérivée de [classe CWinApp](../../mfc/reference/cwinapp-class.md), et il n’inclut pas de prise en charge MFC pour l’ouverture d’un document à partir d’un fichier de disque.

- **Langue de ressource**

   Définit la langue de vos ressources. La liste affiche les langues disponibles sur votre système, comme installés par Visual Studio. Si vous souhaitez sélectionner une langue autre que langue de votre système, le dossier de modèle approprié pour cette langue doit déjà être installé.

   La langue que vous sélectionnez est répercutée dans le **des chaînes localisées** possibilité du [chaînes modèles de Document, Assistant Application MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) page de l’Assistant.

- **Utiliser des bibliothèques Unicode**

   Spécifie si la version non-Unicode ou des bibliothèques MFC est utilisée.

- **Style de projet**

   Indique si votre application possède un standard MFC, Explorateur de fichiers, Visual Studio, ou architecture d’Office et affichage. Pour plus d’informations, consultez [création d’une Application MFC de Style Explorateur de fichiers](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).

   |Option|Description|
   |------------|-----------------|
   |**Norme MFC**|Fournit une architecture d’application MFC standard.|
   |**Explorateur de fichiers**|Implémente un application de type Explorateur de fichier à l’aide d’une fenêtre fractionnée où le volet de gauche est un [à la classe CTreeView](../../mfc/reference/ctreeview-class.md) et le volet de droite est un [CListView (classe)](../../mfc/reference/clistview-class.md).|
   |**Visual Studio**|Implémente une Visual Studio-application qui contient quatre volets ancrables (**affichage des fichiers**, **affichage de classes**, **propriétés**, et **sortie**) qui sont dérivés de [CDockablePane, classe](../../mfc/reference/cdockablepane-class.md) et une fenêtre frame principale qui est dérivée de [CMDIFrameWndEx, classe](../../mfc/reference/cmdiframewndex-class.md) (valeur par défaut).|
   |**Office**|Implémente une application semblable à Office qui contient un ruban dérivé [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md), une barre Outlook qui est dérivée de [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md), une barre de légende qui est dérivée de [CMFCCaptionBar, classe](../../mfc/reference/cmfccaptionbar-class.md)et un frame principal qui est dérivé de [CMDIFrameWndEx, classe](../../mfc/reference/cmdiframewndex-class.md).|

- **Style visuel et couleurs**

   Détermine le style visuel de l’application. Les options ci-dessous sont disponibles :

   - **Windows natif/par défaut**

   - **Office 2003**

   - **Visual Studio 2005**

   - **Office 2007 (thème Blue)**

   - **Office 2007 (thème noir)**

   - **Office 2007 (thème argent)**

   - **Office 2007 (thème cyan)**

- **Activer la commutation de style visuel**

   Spécifie si l’utilisateur peut changer le style visuel de l’application lors de l’exécution, généralement en sélectionnant le style visuel approprié à partir d’un menu ou le ruban.

- **Utilisation des MFC**

   Indique comment créer un lien vers la bibliothèque MFC. Par défaut, MFC est lié en tant qu’une DLL partagée.

   |Option|Description|
   |------------|-----------------|
   |**Utiliser MFC dans une DLL partagée**|Lie la bibliothèque MFC à une application comme une DLL partagée. L’application effectue des appels à la bibliothèque MFC en cours d’exécution. Cette option réduit les besoins en mémoire et de disque d’applications composées de plusieurs fichiers exécutables qui utilisent la bibliothèque MFC. Les applications Win32 et MFC peuvent appeler des fonctions dans votre DLL (valeur par défaut)|
   |**Utiliser MFC dans une bibliothèque statique**|Lie une application à la bibliothèque MFC statique au moment de la génération.|

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

