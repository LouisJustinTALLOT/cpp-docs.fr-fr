---
title: Paramètres du contrôle, Assistant contrôle ActiveX MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.settings
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af5a9f35be36de5e1c72650e83b48e8112469235
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723331"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Paramètres du contrôle, Assistant Contrôle ActiveX MFC
Utilisez cette page de l’Assistant pour spécifier la manière dont le contrôle se comporte. Par exemple, vous pouvez baser le contrôle sur les types de contrôles Windows standards, optimiser son comportement et son apparence ou indiquer que le contrôle peut agir comme un conteneur pour d’autres contrôles.  
  
 Pour plus d’informations sur la sélection des options de cette page pour optimiser l’efficacité du contrôle, consultez [contrôles ActiveX MFC : optimisation](../../mfc/mfc-activex-controls-optimization.md).  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
- **Créer un contrôle basé sur**

   Dans cette liste, vous pouvez sélectionner le type de contrôle à partir de laquelle votre contrôle doit hériter. La liste est un sous-ensemble des classes de contrôle qui sont disponibles pour `CreateWindowEx` et des contrôles courants supplémentaires qui sont spécifiés dans commctrl.h. Votre sélection détermine le style du contrôle dans le `PreCreateWindow` fonctionner dans le *ProjName*fichier Ctrl.cpp. Pour plus d’informations, consultez [contrôles ActiveX MFC : sous-classement d’un contrôle Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
   |Contrôle|Description|  
   |-------------|-----------------|  
   |**BOUTON**|Un contrôle de bouton Windows|  
   |**ZONE DE LISTE DÉROULANTE**|Un contrôle de zone de liste déroulante Windows|  
   |**MODIFIER**|Un contrôle de zone d’édition Windows|  
   |**ZONE DE LISTE**|Un contrôle de zone de liste Windows|  
   |**BARRE DE DÉFILEMENT**|Un contrôle de barre de défilement Windows|  
   |**STATIQUE**|Un contrôle statique Windows|  
   |**msctls_hotkey32**|Un contrôle commun de touche à chaud|  
   |**msctls_progress32**|Une barre de contrôle commun de progression|  
   |**msctls_statusbar32**|Une barre de contrôle commun d’état|  
   |**msctls_trackbar32**|Barre de contrôle commun de suivi|  
   |**msctls_updown32**|Un bouton de sélection numérique (ou up-down) contrôle commun|  
   |**SysAnimate32**|Un contrôle commun d’animation|  
   |**SysHeader32**|Un contrôle commun d’en-tête|  
   |**SysListView32**|Un contrôle commun list view|  
   |**SysTabControl32**|Un contrôle commun d’onglet|  
   |**SysTreeView32**|Un contrôle commun d’arborescence|  
  
- **Actif quand visible**

   Spécifie qu’une fenêtre est créée pour le contrôle lorsqu’il est accessible. Par défaut, le **actif quand visible** option est sélectionnée. Si vous souhaitez différer l’activation du contrôle jusqu'à ce que le conteneur a besoin (par exemple, lorsqu’un utilisateur clique sur la souris), désactivez cette option. Lorsque cette fonctionnalité est désactivée, le contrôle n’entraîne pas le coût de création de la fenêtre jusqu'à ce qu’il est nécessaire. Pour plus d’informations, consultez [la désactivation de l’Option actif quand Visible](../../mfc/turning-off-the-activate-when-visible-option.md).  
  
- **Invisible au moment de l’exécution**

   Spécifie que le contrôle n’a aucun interface utilisateur en cours d’exécution. Un minuteur est un type de contrôle que vous pouvez être invisible.  
  
- **A une boîte de dialogue About**

   Spécifie que le contrôle a le Windows standard **sur** boîte de dialogue qui affiche le numéro de version et les informations de copyright.  
  
   > [!NOTE]
   > Comment l’utilisateur accède à l’aide du contrôle dépend de la façon dont vous avez implémenté l’aide et si vous avez intégré à l’aide du contrôle à l’aide du conteneur. Pour plus d’informations sur l’intégration de l’aide, sur le [MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) site Web, recherchez « Ajout contextuels permettent à un contrôle ActiveX MFC ».  
  
   Lorsque vous sélectionnez cette option, elle insère la `AboutBox` méthode dans la classe de contrôle de projet de contrôle (C*ProjName*Ctrl.cpp) et ajoute AboutBox dans la table de dispatch du projet. Cette option est activée par défaut.  
  
- **Code de dessin optimisé**

   Spécifie que le conteneur restaure automatiquement les objets GDI d’origine une fois que tous les contrôles du conteneur, qui sont dessinés dans le même contexte de périphérique, ont été dessinés. Pour plus d’informations sur cette fonctionnalité, consultez [optimisation de contrôle de dessin](../../mfc/optimizing-control-drawing.md).  
  
- **Activation sans fenêtre**

   Spécifie que le contrôle ne produit pas une fenêtre lorsqu’elle est activée. Activation sans fenêtre autorise les contrôles non rectangulaires ou transparents et un contrôle sans fenêtre requiert nécessite moins de ressources système qu’un contrôle qui a une fenêtre. Un contrôle sans fenêtre n’autorise pas pour un contexte de périphérique non découpé ou l’activation sans scintillement. Les conteneurs qui ont été créés avant 1996 ne gèrent pas l’activation sans fenêtre. Pour plus d’informations sur l’utilisation de cette option, consultez [fournissant l’Activation sans fenêtre](../../mfc/providing-windowless-activation.md).  
  
- **Contexte de périphérique non découpé**

   Substitue [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) dans l’en-tête de contrôle (*projname*ctrl.h) pour désactiver l’appel à `IntersectClipRect` effectuées par `COleControl`. Lorsque vous sélectionnez cette option, il fournit un avantage de vitesse. Si vous sélectionnez **l’activation sans fenêtre**, cette fonctionnalité n’est pas disponible. Pour plus d’informations, consultez [à l’aide d’un contexte de périphérique non découpé](../../mfc/using-an-unclipped-device-context.md).  
  
- **Activation sans scintillement**

   Élimine les opérations de dessin et le scintillement accompagne qui se produisent entre les états actifs et inactifs du contrôle. Si vous sélectionnez **l’activation sans fenêtre**, cette fonctionnalité n’est pas disponible. Lorsque vous définissez cette option, le `noFlickerActivate` indicateur est un des indicateurs qui sont retournés par [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Pour plus d’informations, consultez [fournissant l’Activation sans scintillement](../../mfc/providing-flicker-free-activation.md).  
  
- **Disponible dans la boîte de dialogue Insérer un objet**

   Spécifie que le contrôle sera disponible dans le **insérer un objet** boîte de dialogue pour les conteneurs activés. Lorsque vous sélectionnez cette option, le `afxRegInsertable` indicateur est un des indicateurs qui sont retournés par `AfxOleRegisterControlClass`. À l’aide de la **insérer un objet** boîte de dialogue, un utilisateur peut insérer nouvellement créé ou objets existants dans un document composé.  
  
- **Notifications du pointeur de la souris lorsqu’elle est inactive**

   Active le contrôle pour traiter les notifications du pointeur de la souris, si le contrôle est actif ou non. Lorsque vous sélectionnez cette option, le `pointerInactive` indicateur est un des indicateurs qui sont retournés par [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Pour plus d’informations sur l’utilisation de cette option, consultez [fournissant Interaction souris pendant l’inactivité](../../mfc/providing-mouse-interaction-while-inactive.md).  
  
- **Agit comme un simple contrôle frame**

   Spécifie que le contrôle est un conteneur pour d’autres contrôles en définissant le bit OLEMISC_SIMPLEFRAME pour le contrôle. Pour plus d’informations sur la [MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542) site Web, recherchez « Simple Frame Site relation contenant-contenu ».  
  
- **Charge les propriétés de façon asynchrone**

   Permet une réinitialisation des données asynchrones antérieures et déclenche un nouveau chargement de la propriété asynchrone du contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant contrôle ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Paramètres d’application, Assistant contrôle ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Noms du contrôle, Assistant Contrôle ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

