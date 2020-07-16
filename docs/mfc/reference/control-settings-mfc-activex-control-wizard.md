---
title: Paramètres du contrôle, Assistant Contrôle ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.settings
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
ms.openlocfilehash: 1578ca7f4134e51e0ba0d3c2b247dcafcb0fbd67
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405011"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Paramètres du contrôle, Assistant Contrôle ActiveX MFC

Utilisez cette page de l’Assistant pour spécifier la façon dont vous souhaitez que le contrôle se comporte. Par exemple, vous pouvez baser le contrôle sur des types de contrôles Windows standard, optimiser son comportement et son apparence, ou indiquer que le contrôle peut agir comme un conteneur pour d’autres contrôles.

Pour plus d’informations sur la façon de sélectionner des options sur cette page pour optimiser l’efficacité du contrôle, consultez [contrôles ActiveX MFC : optimisation](../../mfc/mfc-activex-controls-optimization.md).

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Créer un contrôle basé sur**

   Dans cette liste, vous pouvez sélectionner le type de contrôle à partir duquel votre contrôle doit hériter. La liste est un sous-ensemble des classes de contrôle disponibles pour `CreateWindowEx` et des contrôles communs supplémentaires qui sont spécifiés dans commctrl. h. Votre sélection détermine le style du contrôle dans la `PreCreateWindow` fonction dans le fichier *ProjName*Ctrl. cpp. Pour plus d’informations, consultez [contrôles ActiveX MFC : sous-classement d’un contrôle Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

   |Control|Description|
   |-------------|-----------------|
   |**BOUTON**|Contrôle bouton Windows|
   |**COMBOBOX**|Contrôle de zone de liste déroulante Windows|
   |**MODIFIÉS**|Contrôle de zone d’édition Windows|
   |**LISTBOX**|Contrôle de zone de liste Windows|
   |**Rail**|Contrôle de barre de défilement Windows|
   |**STATIQUE**|Contrôle statique Windows|
   |**msctls_hotkey32**|Contrôle commun de touche d’accès rapide|
   |**msctls_progress32**|Contrôle commun de barre de progression|
   |**msctls_statusbar32**|Contrôle commun de barre d’État|
   |**msctls_trackbar32**|Contrôle commun de barre de suivi|
   |**msctls_updown32**|Contrôle commun (ou up-down) de bouton toupie|
   |**SysAnimate32**|Contrôle commun d’animation|
   |**SysHeader32**|Contrôle commun d’en-tête|
   |**SysListView32**|Contrôle commun d’une vue Liste|
   |**SysTabControl32**|Contrôle commun d’onglet|
   |**SysTreeView32**|Contrôle commun d’arborescence|

- **Active quand visible**

   Spécifie qu’une fenêtre est créée pour le contrôle lors de son accès. Par défaut, l’option **active quand** elle est visible est sélectionnée. Si vous souhaitez différer l’activation du contrôle jusqu’à ce que le conteneur l’exige (par exemple, lorsqu’un utilisateur clique sur la souris), désactivez cette option. Lorsque cette fonctionnalité est désactivée, le contrôle ne subit pas de création de fenêtre tant qu’il n’est pas nécessaire. Pour plus d’informations, consultez Désactivation de [l’option Activer quand](../../mfc/turning-off-the-activate-when-visible-option.md)elle est visible.

- **Invisible au moment de l’exécution**

   Spécifie que le contrôle n’a pas d’interface utilisateur au moment de l’exécution. Un minuteur est un type de contrôle que vous souhaitez peut-être invisible.

- **Contient une boîte de dialogue à propos de**

   Spécifie que le contrôle contient la boîte de dialogue **à propos** de Windows standard, qui affiche le numéro de version et les informations de copyright.

   > [!NOTE]
   > La façon dont l’utilisateur accède à l’aide pour le contrôle dépend de la façon dont vous avez implémenté l’aide et si vous avez intégré l’aide du contrôle à l’aide du conteneur.

   Quand vous sélectionnez cette option, elle insère la `AboutBox` méthode Control dans la classe de contrôle de projet (C*ProjName*Ctrl. cpp) et ajoute AboutBox à la table de dispatch du projet. Cette option est activée par défaut.

- **Code de dessin optimisé**

   Spécifie que le conteneur restaure automatiquement les objets GDI d’origine une fois que tous les contrôles de conteneur, qui sont dessinés dans le même contexte de périphérique, ont été dessinés. Pour plus d’informations sur cette fonctionnalité, consultez [optimisation du dessin de contrôle](../../mfc/optimizing-control-drawing.md).

- **Activation sans fenêtre**

   Spécifie que le contrôle ne produit pas de fenêtre lorsqu’il est activé. L’activation sans fenêtre permet d’obtenir des contrôles non rectangulaires ou transparents, et un contrôle sans fenêtre requiert moins de surcharge du système qu’un contrôle dont la fenêtre a besoin. Un contrôle sans fenêtre ne permet pas un contexte de périphérique ou une activation sans scintillement non découpé. Les conteneurs qui ont été créés avant 1996 ne prennent pas en charge l’activation sans fenêtre. Pour plus d’informations sur l’utilisation de cette option, consultez la page mise en place d' [une activation sans fenêtre](../../mfc/providing-windowless-activation.md).

- **Contexte de périphérique (DC) découpé**

   Remplace [COleControl :: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) dans l’en-tête de contrôle (*ProjName*Ctrl. h) pour désactiver l’appel de `IntersectClipRect` `COleControl` . Lorsque vous sélectionnez cette option, vous bénéficiez d’un petit avantage en termes de vitesse. Si vous sélectionnez **activation sans fenêtre**, cette fonctionnalité n’est pas disponible. Pour plus d’informations, consultez [utilisation d’un contexte de périphérique non découpé](../../mfc/using-an-unclipped-device-context.md).

- **Activation sans scintillement**

   Élimine les opérations de dessin et le scintillateur d’accompagnement qui se produisent entre les États actifs et inactifs du contrôle. Si vous sélectionnez **activation sans fenêtre**, cette fonctionnalité n’est pas disponible. Lorsque vous définissez cette option, l' `noFlickerActivate` indicateur est l’un des indicateurs retournés par [COleControl :: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Pour plus d’informations, consultez [fourniture d’une activation sans scintillement](../../mfc/providing-flicker-free-activation.md).

- **Disponible dans la boîte de dialogue Insérer un objet**

   Spécifie que le contrôle sera disponible dans la boîte de dialogue **Insérer un objet** pour les conteneurs activés. Lorsque vous sélectionnez cette option, l' `afxRegInsertable` indicateur est l’un des indicateurs retournés par `AfxOleRegisterControlClass` . À l’aide de la boîte de dialogue **Insérer un objet** , un utilisateur peut insérer des objets nouvellement créés ou existants dans un document composé.

- **Notifications de pointeur de souris en cas d’inactivité**

   Permet au contrôle de traiter les notifications du pointeur de la souris, que le contrôle soit actif ou non. Lorsque vous sélectionnez cette option, l' `pointerInactive` indicateur est l’un des indicateurs retournés par [COleControl :: GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Pour plus d’informations sur l’utilisation de cette option, consultez la page fourniture de l' [interaction avec la souris en cours d’inactivité](../../mfc/providing-mouse-interaction-while-inactive.md).

- **Agit comme un contrôle Frame simple**

   Spécifie que le contrôle est un conteneur pour d’autres contrôles en définissant le bit OLEMISC_SIMPLEFRAME pour le contrôle. Pour plus d’informations, consultez [relation contenant-contenu de site à cadre simple](/windows/win32/com/simple-frame-site-containment).

- **Charge les propriétés de façon asynchrone**

   Active une réinitialisation des données asynchrones précédentes et Initialise une nouvelle charge de la propriété asynchrone du contrôle.

## <a name="see-also"></a>Voir aussi

[Assistant contrôle ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Paramètres de l’application, Assistant contrôle ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Noms des contrôles, Assistant contrôle ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)
