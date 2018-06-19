---
title: Type d’application, Assistant Application MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.apptype
dev_langs:
- C++
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5708e823c57ecdb8470a398c4192cba1a5b6e411
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353437"
---
# <a name="application-type-mfc-application-wizard"></a>Type d'application, Assistant Application MFC
Utilisez cette page de la [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md) pour concevoir et ajouter des fonctionnalités de base pour une application MFC.  
  
 **Type d’application**  
 Spécifie le type de prise en charge de document que vous souhaitez créer dans votre application. Le type d’application sélectionné détermine les options d’interface utilisateur qui sont disponibles pour votre application. Consultez [fonctionnalités d’Interface utilisateur, Assistant Application MFC](../../mfc/reference/user-interface-features-mfc-application-wizard.md) pour plus d’informations.  
  
 Pour plus d’informations sur les types de documents, consultez :  
  
-   [SDI et MDI](../../mfc/sdi-and-mdi.md)  
  
-   [Fenêtres frame](../../mfc/frame-windows.md)  
  
-   [Classes de fenêtre frame](../../mfc/frame-window-classes.md)  
  
-   [Documents, vues et le Framework](../../mfc/documents-views-and-the-framework.md)  
  
-   [Boîtes de dialogue](../../mfc/dialog-boxes.md)  
  
|Option|Description|  
|------------|-----------------|  
|**Document unique**|Crée une architecture d’interface (monodocument SDI) de document unique pour votre application, où une classe d’affichage est basée sur [classe CView](../../mfc/reference/cview-class.md). Vous pouvez modifier la classe de base pour l’affichage dans le [Classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de l’Assistant. Pour créer une application basée sur le formulaire, par exemple, utilisez [CFormView, classe](../../mfc/reference/cformview-class.md) pour la classe d’affichage.<br /><br /> Dans ce type d’application, la fenêtre de document frame peut contenir qu’un seul document.|  
|**Plusieurs documents**|Crée une architecture de votre application, où une classe d’affichage est basée sur l’interface (multidocument MDI) document `CView`. Vous pouvez modifier la classe de base pour l’affichage dans le **Classes générées** page de l’Assistant. Pour créer une application basée sur le formulaire, par exemple, utilisez `CFormView` pour la classe d’affichage.<br /><br /> Dans ce type d’application, la fenêtre de document frame peut contenir plusieurs fenêtres enfants.|  
|**Documents avec onglet**|Place chaque document dans un onglet distinct.|  
|**Boîte de dialogue en fonction**|Crée une architecture basée sur la boîte de dialogue pour votre application avec une classe de boîte de dialogue est basée sur `CDialog`. (Pour créer une boîte de dialogue HTML, activez la case **boîte de dialogue utilisation HTML**.)|  
|**Utilisez la boîte de dialogue HTML**|Pour les applications boîte dialogue uniquement. Dérive la classe de boîte de dialogue de [classe CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) au lieu de [CDialog (classe)](../../mfc/reference/cdialog-class.md). Si vous cochez cette case, `CDHtmlDialog` est répertorié dans le **classe de Base** zone le [Classes générées, Assistant Application MFC](../../mfc/reference/generated-classes-mfc-application-wizard.md) page de l’Assistant.<br /><br /> A `CDHtmlDialog`-boîte de dialogue dérivée affiche les boîtes de dialogue HTML, échange des données avec du code HTML contrôlent et gère les événements HTML.|  
|**Plusieurs documents de niveau supérieur**|Crée une architecture niveau supérieur pour votre application, où une classe d’affichage est basée sur `CView`.<br /><br /> Dans ce type d’application, lorsqu’un utilisateur clique **nouveau** (ou **nouveau Frame**) sur le **fichier** menu, l’application crée une fenêtre dont le parent est implicitement le bureau. Le nouveau frame de document apparaît dans la barre des tâches et n’est pas limité à la zone cliente de la fenêtre d’application.|  
  
 **Prise en charge de l’architecture de document/vue**  
 Spécifie s’il faut inclure l’architecture document/vue dans votre application à l’aide de la [CDocument (classe)](../../mfc/reference/cdocument-class.md) et [CView (classe)](../../mfc/reference/cview-class.md) (par défaut). Désactivez cette case à cocher si vous portez une application non-MFC ou si vous souhaitez réduire la taille de l’exécutable compilé. Par défaut, une application sans architecture document/vue est dérivée de [CWinApp (classe)](../../mfc/reference/cwinapp-class.md), et il n’inclut pas de prise en charge MFC pour l’ouverture d’un document à partir d’un fichier de disque.  
  
 **Langue de ressource**  
 Définit la langue de vos ressources. La liste affiche les langues disponibles sur votre système, installé par Visual Studio. Si vous souhaitez sélectionner une autre langue que la langue de votre système, le dossier de modèle approprié pour cette langue doit déjà être installé. Pour plus d’informations sur l’installation des ressources de langue différentes par défaut disponibles dans le **langue de ressource** liste, consultez [prise en charge de l’Assistant pour d’autres langages](../../ide/wizard-support-for-other-languages.md).  
  
 La langue que vous sélectionnez est répercutée dans le **des chaînes localisées** option de le [chaînes modèles de Document, Assistant Application MFC](../../mfc/reference/document-template-strings-mfc-application-wizard.md) page de l’Assistant.  
  
 **Utiliser des bibliothèques Unicode**  
 Spécifie si la version non-Unicode ou des bibliothèques MFC est utilisée.  
  
 **Style de projet**  
 Indique si votre application possède un standard MFC, l’Explorateur de fichiers, Visual Studio, ou Office l’architecture et affichage. Pour plus d’informations, consultez [création d’une Application MFC de Style Explorateur de fichiers](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md).  
  
|Option|Description|  
|------------|-----------------|  
|**Norme MFC**|Fournit une architecture d’application MFC standard.|  
|**Explorateur de fichiers**|Implémente un application de type Explorateur de fichier à l’aide d’une fenêtre fractionnée où le volet de gauche est un [CTreeView (classe)](../../mfc/reference/ctreeview-class.md) et le volet de droite est un [CListView (classe)](../../mfc/reference/clistview-class.md).|  
|**Visual Studio**|Implémente une application Visual Studio de type qui contient quatre volets ancrables (**affichage des fichiers**, **affichage de classes**, **propriétés**, et **sortie**) qui sont dérivés de [classe CDockablePane](../../mfc/reference/cdockablepane-class.md) et une fenêtre frame principale qui est dérivée de [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md) (par défaut).|  
|**Office**|Implémente une application de type Office qui contient un ruban dérivé [classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md), une barre Outlook qui est dérivée de [CMFCOutlookBar, classe](../../mfc/reference/cmfcoutlookbar-class.md), une barre de légende qui est dérivée de [CMFCCaptionBar, classe](../../mfc/reference/cmfccaptionbar-class.md)et un frame principal qui est dérivé de [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md).|  
  
 **Style visuel et couleurs**  
 Détermine le style visuel de l’application. Les options ci-dessous sont disponibles :  
  
-   **Windows natif/par défaut**  
  
-   **Office 2003**  
  
-   **Visual Studio 2005**  
  
-   **Office 2007 (thème Blue)**  
  
-   **Office 2007 (thème noir)**  
  
-   **Office 2007 (thème argent)**  
  
-   **Office 2007 (thème cyan)**  
  
 **Activer le changement de style visuel**  
 Spécifie si l’utilisateur peut modifier le style visuel de l’application lors de l’exécution, généralement en sélectionnant le style visuel approprié à partir d’un menu ou un ruban.  
  
 **Utilisation des MFC**  
 Indique comment créer un lien vers la bibliothèque MFC. Par défaut, MFC est lié en tant que DLL partagé.  
  
|Option|Description|  
|------------|-----------------|  
|**Utiliser les MFC dans une DLL partagée**|La bibliothèque MFC est liée à une application en tant que DLL partagé. L’application effectue des appels à la bibliothèque MFC au moment de l’exécution. Cette option réduit les besoins en mémoire et espace disque des applications qui se composent de plusieurs fichiers exécutables qui utilisent la bibliothèque MFC. Les applications Win32 et MFC peuvent appeler des fonctions dans votre DLL (valeur par défaut)|  
|**Utiliser les MFC dans une bibliothèque statique**|Lie une application à la bibliothèque MFC statique au moment de la génération.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

