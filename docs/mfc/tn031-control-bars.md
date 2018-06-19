---
title: 'TN031 : Barres de contrôles | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.bars
dev_langs:
- C++
helpviewer_keywords:
- control bars [MFC], styles
- CStatusBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], deriving from
- control bars [MFC], classes [MFC]
- CDialogBar class [MFC], Tech Note 31 usage
- CToolBar class [MFC], Tech Note 31 usage
- TN031
- styles [MFC], control bars
ms.assetid: 8cb895c0-40ea-40ef-90ee-1dd29f34cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1d5cc113177a9653e709c14f66682959276e7ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385324"
---
# <a name="tn031-control-bars"></a>TN031 : Barres de contrôles
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note décrit les classes générales de barres de contrôles dans MFC : [CControlBar](#_mfcnotes_ccontrolbar), [CStatusBar](#_mfcnotes_cstatusbar), [CToolBar](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)et **CDockBar**.  
  
## <a name="_mfcnotes_ccontrolbar"></a> CControlBar 
  
 Un **ControlBar** est une classe dérivée de `CWnd`qui :  
  
-   Est aligné en haut ou en bas d’une fenêtre frame.  
  
-   Peut contenir des éléments enfants qui sont soit des contrôles basés sur HWND (par exemple `CDialogBar`), soit des éléments non basés sur`HWND` (par exemple `CToolBar`ou `CStatusBar`).  
  
 Les barres de contrôles prennent en charge les styles supplémentaires suivants :  
  
- `CBRS_TOP` (valeur par défaut) Épingler la barre de contrôle en haut.  
  
- `CBRS_BOTTOM` Épingler la barre de contrôle en bas.  
  
- `CBRS_NOALIGN` Ne pas repositionner la barre de contrôle quand le parent est redimensionné.  
  
 Les classes dérivées de `CControlBar` fournissent des implémentations plus intéressantes :  
  
- `CStatusBar` Une barre d’état. Les éléments sont des volets de barre d’état contenant du texte.  
  
- `CToolBar` Une barre d’outils. Les éléments sont des boutons de bitmap alignés sur une ligne.  
  
- `CDialogBar` Un cadre de barre d’outils contenant des commandes Windows standard (créés à partir d’une ressource de modèle de boîte de dialogue).  
  
- **CDockBar** Une zone d’ancrage généralisée pour d’autres objets dérivés de `CControlBar` . Les variables et fonctions membres spécifiques disponibles dans cette classe sont susceptibles de changer dans les versions ultérieures.  
  
 L’ensemble des fenêtres et des objets des barres de contrôles seront des fenêtres enfants d’une fenêtre de frame parente. Ils sont généralement ajoutés comme frères à la zone cliente du frame (par exemple, un client MDI ou une vue). L’ID de fenêtre enfant d’une barre de contrôle est important. La disposition par défaut de la barre de contrôle fonctionne uniquement pour les barres de contrôles dont l’ID est compris dans la plage allant de **AFX_IDW_CONTROLBAR_FIRST** à **AFX_IDW_CONTROLBAR_LAST**. Notez que même s’il existe une plage de 256 ID de barres de contrôles, les 32 premiers sont spéciaux car ils sont directement pris en charge par l’architecture d’aperçu avant impression.  
  
 La classe `CControlBar` fournit une implémentation standard pour :  
  
-   L’alignement de la barre de contrôle en haut, en bas ou de chaque côté du frame.  
  
-   L’allocation des tableaux d’éléments de contrôle.  
  
-   La prise en charge de l’implémentation des classes dérivées.  
  
 Les objets de barres de contrôles C++ sont généralement incorporés comme membres d’une classe dérivée de `CFrameWnd` et sont nettoyés quand le `HWND` parent et l’objet sont détruits. Si vous devez allouer un objet de barre de contrôle sur le tas, vous pouvez simplement affecter la valeur **TRUE** au membre **m_bAutoDestruct** pour faire en sorte que la barre de contrôle «**supprime cela**» quand le `HWND` est détruit.  
  
> [!NOTE]
>  Si vous créez vos propres classes dérivées de `CControlBar`, plutôt que d’utiliser l’une des classes dérivées du document MFC, telles que `CStatusBar`, `CToolBar`ou `CDialogBar`, vous devez définir le membre de données `m_dwStyle` . Vous pouvez le faire dans la substitution de **Create**:  
  
```  
// CMyControlBar is derived from CControlBar  
BOOL CMyControlBar::Create(CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID)  
{  
    m_dwStyle = dwStyle;  
 
 .  
 .  
 .  
}  
```  
  
 **Algorithme de disposition de barre de contrôle**  
  
 L’algorithme de disposition de barre de contrôle est très simple. La fenêtre frame envoie un message **WM_SIZEPARENT** à tous les enfants compris dans la plage de barre de contrôle. Un pointeur vers le rectangle client du parent est passé en même temps que ce message. Ce message est envoyé aux éléments enfants dans l’ordre de plan. Les enfants de la barre de contrôle utilisent ces informations pour se positionner et pour réduire la taille de la zone cliente du parent. Le rectangle final conservé pour la zone cliente normale (moins les barres de contrôles) sert à positionner la fenêtre cliente principale (généralement un client MDI, une vue ou une fenêtre fractionnée).  
  
 Pour plus d’informations, consultez `CWnd::RepositionBars` et `CFrameWnd::RecalcLayout` .  
  
 Les messages Windows privés du document MFC, notamment **WM_SIZEPARENT**, sont documentés dans la [Note technique 24](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## <a name="_mfcnotes_cstatusbar"></a>  CStatusBar  
  
 Une barre d’état est une barre de contrôle qui comporte une ligne de volets de sortie de texte. Il existe deux manières courantes d’utiliser des volets de sortie de texte :  
  
-   Comme ligne de message  
  
     (par exemple, la ligne de message d’aide du menu standard). Ils sont généralement accessibles par un index de base 0  
  
-   Comme indicateurs d’état  
  
     (par exemple, les indicateurs MAJ, NUM et DÉFIL). Ils sont généralement accessibles par ID de chaîne/commande.  
  
 La police de la barre d’état est 10 points MS Sans Serif (dictée par le Guide de conception d’application d’interface Windows ou par la meilleure correspondance du mappeur de police pour une police proportionnelle Swiss 10 points). Sur certaines versions de Windows, comme la version japonaise, les polices sélectionnées sont différentes.  
  
 Les couleurs utilisées dans la barre d’état sont également conformes à la recommandation du Guide de conception d’application d’interface Windows. Ces couleurs ne sont pas codées en dur. Elles sont modifiées de manière dynamique en réponse à la personnalisation par l’utilisateur dans le Panneau de configuration.  
  
|Élément|Valeur COLOR Windows|RVB par défaut|  
|----------|-------------------------|-----------------|  
|Arrière-plan de la barre d’état|**COLOR_BTNFACE**|RGB(192, 192, 192)|  
|Texte de la barre d'état|**COLOR_BTNTEXT**|RGB(000, 000, 000)|  
|Bords supérieur et gauche de la barre d’état|**COLOR_BTNHIGHLIGHT**|RGB(255, 255, 255)|  
|Bords inférieur et droit de la barre d’état|**COLOR_BTNSHADOW**|RGB(128, 128, 128)|  
  
 **Prise en charge de CCmdUI pour CStatusBar**  
  
 Les indicateurs sont généralement mis à jour par le biais du mécanisme `ON_UPDATE_COMMAND_UI` . Pendant les périodes d’inactivité, la barre d’état appelle le gestionnaire `ON_UPDATE_COMMAND_UI` avec l’ID de chaîne du volet d’indicateur.  
  
 Le gestionnaire `ON_UPDATE_COMMAND_UI` peut appeler :  
  
- **Enable**: pour activer ou désactiver le volet. Un volet désactivé est identique à un volet activé, sauf que le texte est invisible (autrement dit, l’indicateur de texte est désactivé).  
  
- **SetText**: pour modifier le texte. Faites attention si vous utilisez cette option, car le volet n’est pas redimensionné automatiquement.  
  
 Pour plus d’informations sur les API de création et de personnalisation [, consultez la classe](../mfc/reference/cstatusbar-class.md) CStatusBar *dans la* Référence de la bibliothèque de classes `CStatusBar` . La plupart des opérations de personnalisation des barres d’état doivent être effectuées avant que la barre d’état soit initialement rendue visible.  
  
 La barre d’état prend en charge un seul volet extensible, généralement le premier volet. La taille de ce volet est vraiment une taille minimale. Si la taille de la barre d’état est supérieure à la taille minimale de tous les volets, toute largeur supplémentaire est accordée au volet extensible. L’application par défaut avec une barre d’état comporte des indicateurs alignés à droite pour MAJ, NUM et DÉFIL, puisque le premier volet est extensible.  
  
## <a name="_mfcnotes_ctoolbar"></a>  CToolBar  
  
 Une barre d’outils est une barre de contrôle comportant une ligne de boutons bitmap pouvant inclure des séparateurs. Deux styles de boutons sont pris en charge : les boutons de commande et les cases à cocher. Vous pouvez créer une fonctionnalité de groupe de cases d’option avec des cases à cocher et `ON_UPDATE_COMMAND_UI`.  
  
 Tous les boutons de bitmap dans la barre d’outils proviennent d’une seule bitmap. Cette bitmap doit contenir une image ou un glyphe pour chaque bouton. En général, l’ordre des images/glyphes dans la bitmap est le même que celui dans lequel ils seront dessinés à l’écran. (Cela peut être modifié à l’aide des API de personnalisation.)  
  
 Chaque bouton doit avoir la même taille. La valeur par défaut est la taille standard de 24x22 pixels. Chaque image/glyphe doit avoir la même taille et doit être côte à côte dans la bitmap. La taille d’image/glyphe par défaut est de 16x15 pixels. Ainsi, pour une barre d’outils avec 10 boutons (de taille standard), vous avez besoin d’une bitmap de 160 pixels de large sur 15 pixels de haut.  
  
 Chaque bouton a une seule et unique image/glyphe. Les différents états et styles des boutons (par exemple enfoncé, activé, désactivé et indéterminé) sont générés par un algorithme à partir de cette image/glyphe. En théorie, vous pouvez utiliser n’importe quelle bitmap ou DIB en couleur. L’algorithme permettant de générer les différents états des boutons fonctionne mieux si l’image d’origine est en nuances de gris. Pour obtenir des exemples, consultez les boutons de barres d’outils standard et les images clipart de boutons de barres d’outils fournis dans l’exemple général MFC [CLIPART](../visual-cpp-samples.md) .  
  
 Les couleurs utilisées dans la barre d’outils sont également conformes à la recommandation du Guide de conception d’application d’interface Windows. Ces couleurs ne sont pas codées en dur. Elles sont modifiées de manière dynamique en réponse à la personnalisation par l’utilisateur dans le Panneau de configuration.  
  
|Élément|Valeur COLOR Windows|RVB par défaut|  
|----------|-------------------------|-----------------|  
|Arrière-plan de la barre d’outils|**COLOR_BTNFACE**|RGB(192,192,192)|  
|Bords supérieur et gauche des boutons de barre d’outils|**COLOR_BTNHIGHLIGHT**|RGB(255,255,255)|  
|Bords inférieur et droit des boutons de barre d’outils|**COLOR_BTNSHADOW**|RGB(128,128,128)|  
  
 De plus, les boutons bitmap de la barre d’outils sont recoloriés comme s’il s’agissait de contrôles de boutons Windows standard. Ce recoloriage a lieu quand la bitmap est chargée à partir de la ressource et en réponse à une modification des couleurs système suite à une personnalisation par l’utilisateur dans le Panneau de configuration. Les couleurs suivantes dans une bitmap de barre d’outils sont recoloriées automatiquement. Utilisez-les avec précaution. Si vous ne souhaitez pas qu’une partie de votre bitmap soit recoloriée, utilisez une couleur qui se rapproche de l’une des valeurs RVB mappées. Le mappage est effectué en fonction des valeurs RVB exactes.  
  
|Valeur RVB|Valeur COLOR mappée de manière dynamique|  
|---------------|------------------------------------|  
|RGB(000, 000, 000)|COLOR_BTNTEXT|  
|RGB(128, 128, 128)|COLOR_BTNSHADOW|  
|RGB(192, 192, 192)|COLOR_BTNFACE|  
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|  
  
 Pour plus d’informations sur les API de création et de personnalisation [, consultez la classe](../mfc/reference/ctoolbar-class.md) CToolBar *dans la* Référence de la bibliothèque de classes `CToolBar` . La plupart des opérations de personnalisation des barres d’outils doivent être effectuées avant que la barre d’outils soit initialement rendue visible.  
  
 Vous pouvez utiliser les API de personnalisation pour ajuster les ID de boutons, les styles, la largeur d’espacement et l’image/le glyphe utilisé(e) pour les boutons. Par défaut, vous n’êtes pas obligé d’utiliser ces API.  
  
## <a name="ccmdui-support-for-ctoolbar"></a>Prise en charge de CCmdUI pour CToolBar  
 Les boutons de barre d’outils sont toujours mis à jour par le biais du mécanisme `ON_UPDATE_COMMAND_UI` . Pendant les périodes d’inactivité, la barre d’outils appelle le gestionnaire `ON_UPDATE_COMMAND_UI` avec l’ID de commande de ce bouton. `ON_UPDATE_COMMAND_UI` n’est pas appelée pour les séparateurs, mais elle est appelée pour les boutons de commande et les cases à cocher.  
  
 Le gestionnaire `ON_UPDATE_COMMAND_UI` peut appeler :  
  
- **Enable**: pour activer ou désactiver le bouton. Cela fonctionne pareillement pour les boutons de commande et les cases à cocher.  
  
- `SetCheck`: pour définir l’état d’activation d’un bouton. Si vous appelez cette fonction pour un bouton de barre d’outils, il est converti en case à cocher. `SetCheck` prend un paramètre qui peut être 0 (désactivé), 1 (activé) ou 2 (indéterminé)  
  
- `SetRadio`: forme abrégée de `SetCheck`.  
  
 Les boutons de case à cocher sont des boutons de case à cocher « AUTO ». Autrement dit, quand l’utilisateur appuie dessus, ils changent d’état immédiatement. « Activé » correspond à l’état enfoncé. L’interface utilisateur n’intègre aucun moyen de faire basculer un bouton à l’état « indéterminé ». Vous devez le faire par le biais du code.  
  
 Les API de personnalisation vous permettent de modifier l’état d’un bouton de barre d’outils donné. Dans l’idéal, vous devez modifier ces états dans le gestionnaire `ON_UPDATE_COMMAND_UI` de la commande représentée par le bouton de barre d’outils. N’oubliez pas que le traitement des temps d’inactivité change l’état des boutons de barre d’outils avec le gestionnaire `ON_UPDATE_COMMAND_UI` . Ainsi, toute modification apportée à ces états par le biais de SetButtonStyle peut être perdue après la période d’inactivité suivante.  
  
 Les boutons de barre d’outils envoient des messages **WM_COMMAND** comme des boutons ou des éléments de menu normaux, qui sont normalement gérés par un gestionnaire `ON_COMMAND` dans la même classe que celle qui fournit le gestionnaire `ON_UPDATE_COMMAND_UI` .  
  
 Quatre styles de boutons de barre d’outils (valeurs TBBS_) sont utilisés pour les états d’affichage :  
  
-   TBBS_CHECKED : La case à cocher est actuellement activée.  
  
-   TBBS_INDETERMINATE : La case à cocher est actuellement indéterminée.  
  
-   TBBS_DISABLED : Le bouton est actuellement désactivé.  
  
-   TBBS_PRESSED : Le bouton est actuellement enfoncé.  
  
 Les six styles de bouton officiels du Guide de conception d’application d’interface Windows sont représentés par les valeurs TBBS suivantes :  
  
-   Activé = 0  
  
-   Bouton de souris enfoncé = TBBS_PRESSED (&#124; tout autre style)  
  
-   Désactivé = TBBS_DISABLED  
  
-   Enfoncé = TBBS_CHECKED  
  
-   Enfoncé désactivé = TBBS_CHECKED &#124; TBBS_DISABLED  
  
-   Indéterminé = TBBS_INDETERMINATE  
  
##  <a name="_mfcnotes_cdialogbar"></a> CDialogBar  
 Une barre de boîte de dialogue est une barre de contrôle qui contient des commandes Windows standard. Elle agit comme une boîte de dialogue car elle contient les contrôles et prend en charge la tabulation entre eux. Elle agit également comme une boîte de dialogue car elle utilise un modèle de boîte de dialogue pour représenter la barre.  
  
 Un `CDialogBar` est utilisé pour la barre d’outils Aperçu avant impression, qui contient des contrôles de commande standard.  
  
 Utiliser un `CDialogBar` revient à utiliser un `CFormView`. Vous devez définir un modèle de boîte de dialogue pour la barre de boîte de dialogue et supprimer tous les styles à l’exception de **WS_CHILD**. Notez que la boîte de dialogue ne doit pas être visible.  
  
 Les notifications de contrôle pour un `CDialogBar` sont envoyés au parent de la barre de contrôle (tout comme des boutons de barre d’outils).  
  
## <a name="ccmdui-support-for-cdialogbar"></a>Prise en charge de CCmdUI pour CDialogBar  
 Vous devez mettre à jour les boutons de barre de boîte de dialogue par le biais du mécanisme du gestionnaire `ON_UPDATE_COMMAND_UI` . À la durée d’inactivité, la barre de boîte de dialogue appelle le `ON_UPDATE_COMMAND_UI` gestionnaire avec l’ID de commande de tous les boutons qui ont un ID > = 0 x 8000 (autrement dit, dans la plage d’ID de commandes).  
  
 Le gestionnaire `ON_UPDATE_COMMAND_UI` peut appeler :  
  
-   Enable : pour activer ou désactiver le bouton.  
  
-   SetText : pour modifier le texte du bouton.  
  
 Vous pouvez effectuer une personnalisation par le biais des API du gestionnaire de fenêtre standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

