---
title: Ajout, modification ou suppression de contrôles
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.dialog
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: b4edb5b7a51e4f6d368759ebc2e05a1cc585f19a
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742750"
---
# <a name="adding-editing-or-deleting-controls"></a>Ajout, modification ou suppression de contrôles

À l’aide de la **boîte de dialogue** éditeur, vous pouvez ajouter, redimensionner, modifier et supprimer des contrôles dans les boîtes de dialogue. Vous pouvez également modifier les propriétés d’un contrôle, telles que son ID, ou s’il est visible initialement en cours d’exécution.

Le **boîte de dialogue Éditeur** onglet s’affiche dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox) lorsque vous travaillez dans le **boîte de dialogue** éditeur. Vous pouvez également personnaliser le **boîte à outils** fenêtre pour faciliter son utilisation. Pour plus d’informations, consultez [à l’aide de la boîte à outils](/visualstudio/ide/using-the-toolbox) et [afficher ou masquer la fenêtre Boîte à outils](showing-or-hiding-the-dialog-editor-toolbar.md).

Vous pouvez utiliser le menu contextuel dans le **boîte de dialogue** éditeur permet d’ajouter rapidement inscrit les contrôles ActiveX à une boîte de dialogue, et vous pouvez ajouter des contrôles ActiveX les **boîte à outils** pour y accéder rapidement.

Les contrôles standards disponibles dans le **boîte à outils** valeur par défaut, les événements sont :

|Nom du contrôle|Événement par défaut|
|---|---|
|[Contrôle de bouton](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Contrôle de case à cocher](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Contrôle Combo Box](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Contrôle d’édition](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Contrôle Group box|(Non applicable)|
|[Contrôle List Box](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Contrôle Radio Button](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Contrôle Static Text](../mfc/reference/cstatic-class.md)|(Non applicable)|
|[Contrôle d’image](../mfc/reference/cpictureholder-class.md)|(Non applicable)|
|[Contrôle Rich Edit 2.0](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[Contrôle de barre de défilement](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

Pour plus d’informations sur l’utilisation de la **RichEdit 1.0** contrôler avec MFC, consultez [à l’aide du contrôle RichEdit 1.0 avec MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) et [enrichi modifier des exemples de contrôle](../mfc/rich-edit-control-examples.md).

Le [contrôles communs Windows](../mfc/controls-mfc.md) disponibles dans le **boîte à outils** fournissent des fonctionnalités améliorées dans votre application. Elles comprennent :

|Nom du contrôle|Événement par défaut|
|---|---|
|[Contrôle Slider](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Contrôle Spin](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Contrôle de progression](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Contrôle Hot Key](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Contrôle de liste](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Contrôle d’arborescence](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Contrôle onglet](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Contrôle Animation](../mfc/using-an-animation-control.md)|ACN_START|
|[Contrôle Date Time Picker](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Contrôle Month Calendar](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[Contrôle de l’adresse IP](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Contrôle Extended Combo Box](../mfc/creating-an-extended-combo-box-control.md)||
|[Contrôle personnalisé](custom-controls-in-the-dialog-editor.md)|TTN_GETDISPINFO|

Pour plus d’informations, consultez [Classes de contrôle](../mfc/control-classes.md), [Classes de boîte de dialogue](../mfc/dialog-box-classes.md), et [Styles de barre de défilement](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-add-a-control"></a>Pour ajouter un contrôle

Pour ajouter des contrôles à votre nouvelle boîte de dialogue, faites glisser des contrôles à partir de la **boîte à outils** à la boîte de dialogue que vous créez. Vous pouvez ensuite déplacer les contrôles ou modifier leur taille et leur forme.

Vous pouvez ajouter des contrôles personnalisés à la boîte de dialogue en sélectionnant le **contrôle personnalisé** icône dans le **boîte à outils** et faites-la glisser vers votre boîte de dialogue. Pour ajouter un **Syslink** contrôler, ajoutez un contrôle personnalisé, puis modifier le contrôle **classe** propriété **Syslink**. Cette action entraîne les propriétés actualiser et afficher le **Syslink** propriétés du contrôle. Pour plus d’informations sur la classe wrapper MFC, consultez [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

### <a name="to-add-a-control-to-a-dialog-box"></a>Pour ajouter un contrôle à une boîte de dialogue

1. Assurez-vous que la fenêtre avec onglet de la boîte de dialogue représente le document actif dans le cadre de l’éditeur. Si une boîte de dialogue n’est pas le document actif, vous ne voyez pas le **onglet de boîte de dialogue Éditeur** dans le **boîte à outils**.

1. Sur le **boîte de dialogue Éditeur** onglet de la **boîte à outils** fenêtre, sélectionnez le contrôle souhaité, puis :

   Sélectionnez la boîte de dialogue à l’emplacement où vous souhaitez placer le contrôle. Le contrôle s’affiche où vous avez sélectionné.

   \- ou -

   Faites glisser le contrôle à partir de la **boîte à outils** fenêtre à l’emplacement sur votre boîte de dialogue.

   \- ou -

   Double-cliquez sur le contrôle dans le **boîte à outils** fenêtre (il apparaît dans votre boîte de dialogue), puis repositionnez le contrôle à l’emplacement de votre choix.

### <a name="to-add-multiple-controls"></a>Pour ajouter plusieurs contrôles

1. Tout en maintenant enfoncée la **Ctrl** enfoncée, sélectionnez un contrôle dans le **boîte à outils** fenêtre.

1. Mise en production la **Ctrl** la clé, sélectionnez la boîte de dialogue autant de fois que vous souhaitez ajouter ce contrôle.

1. Appuyez sur **ÉCHAP** pour arrêter.

### <a name="to-size-a-control-while-you-add-it"></a>Pour dimensionner un contrôle pendant son ajout

1. Sélectionnez un contrôle dans le **boîte à outils** fenêtre.

1. Placez votre curseur (qui apparaît comme forme de croix) à l’emplacement souhaité pour le coin supérieur gauche du nouveau contrôle doivent se trouver sur votre boîte de dialogue.

1. Sélectionnez et maintenez le bouton de la souris pour ancrer le coin supérieur gauche de votre contrôle sur la boîte de dialogue, puis faites glisser le curseur vers la droite et vers le bas jusqu'à ce que le contrôle est la taille voulue.

   > [!NOTE]
   > Vous pouvez ancrer n’importe lequel des quatre coins du contrôle que vous dessinez. Cette procédure utilisé le coin supérieur gauche comme exemple.

1. Relâchez le bouton de la souris. Le contrôle est placé dans la boîte de dialogue dans la taille spécifiée.

   > [!TIP]
   > Vous pouvez redimensionner le contrôle après le déposant sur la boîte de dialogue en déplaçant les poignées de redimensionnement sur la bordure du contrôle. Pour plus d’informations, consultez [dimensionnement de contrôles individuels](../windows/sizing-individual-controls.md).

### <a name="to-add-an-activex-control"></a>Pour ajouter un contrôle ActiveX

Avec Visual Studio, vous pouvez insérer des contrôles ActiveX dans votre boîte de dialogue. Pour plus d’informations, consultez [contrôles ActiveX MFC](../mfc/mfc-activex-controls.md) et [conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md).

Le **insérer un contrôle ActiveX** boîte de dialogue permet d’insérer des contrôles ActiveX dans votre boîte de dialogue lors de l’utilisation du [éditeur de boîte de dialogue](../windows/dialog-editor.md). Cette boîte de dialogue contient les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Contrôle ActiveX**|Affiche une liste de contrôles Active X. Insertion d’un contrôle à partir de cette boîte de dialogue ne génère pas une classe wrapper. Si vous avez besoin d’une classe wrapper, utilisez [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) pour en créer une (pour plus d’informations, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)). Si un contrôle ActiveX n’apparaît pas dans cette boîte de dialogue, essayez d’installer le contrôle selon les instructions du fournisseur.|
|**Chemin d’accès**|Affiche le fichier dans lequel le contrôle ActiveX est trouvé.|

#### <a name="to-see-the-activex-controls-available"></a>Pour afficher les contrôles ActiveX disponibles

1. Ouvrez une boîte de dialogue dans l’Éditeur de boîtes de dialogue.

1. Avec le bouton droit n’importe où dans le corps de la boîte de dialogue.

1. Dans le menu contextuel, sélectionnez **insérer un contrôle ActiveX**.

   Le **insérer un contrôle ActiveX** boîte de dialogue apparaît, affichant tous les contrôles ActiveX sur votre système. En bas de la boîte de dialogue figure le chemin d’accès au fichier de contrôle ActiveX.

#### <a name="to-add-an-activex-control-to-a-dialog-box"></a>Pour ajouter un contrôle ActiveX à une boîte de dialogue

1. Dans le **insérer un contrôle ActiveX** boîte de dialogue, sélectionnez le contrôle que vous souhaitez ajouter à votre boîte de dialogue, puis sélectionnez **OK**.

   Le contrôle apparaît dans la boîte de dialogue, où vous pouvez le modifier ou créer des gestionnaires comme vous le feriez pour n’importe quel autre contrôle.

   > [!NOTE]
   > Vous pouvez ajouter des contrôles ActiveX les **boîte à outils** fenêtre pour pouvoir accéder facilement.

   > [!CAUTION]
   > Il se peut que la distribution de tous les contrôles ActiveX sur votre système ne soit pas autorisée juridiquement. Reportez-vous au contrat de licence du logiciel qui a installé les contrôles ou contactez l’éditeur du logiciel.

## <a name="to-edit-a-control"></a>Pour modifier un contrôle

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Pour modifier les propriétés d’un contrôle ou de contrôles

1. Dans la boîte de dialogue, sélectionnez le contrôle que vous souhaitez modifier.

   > [!NOTE]
   > Si vous sélectionnez plusieurs contrôles, uniquement les propriétés communes aux contrôles sélectionnés peuvent être modifiées.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), modifier les propriétés de votre contrôle.

   > [!NOTE]
   > Lorsque vous définissez la **Bitmap** propriété pour un bouton, une case d’option ou un contrôle de case à cocher égal à **True**, le style BS_BITMAP est implémenté pour votre contrôle. Pour plus d’informations, consultez [Styles de boutons](../mfc/reference/styles-used-by-mfc.md#button-styles). Pour obtenir un exemple d’association d’une image bitmap à un contrôle, consultez [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Bitmaps n’apparaissent pas sur votre contrôle pendant que vous êtes dans le **boîte de dialogue** éditeur de ressources.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Pour annuler les modifications apportées aux propriétés d’un contrôle

1. Assurez-vous que le contrôle a le focus dans le **boîte de dialogue** éditeur.

1. Choisissez **Annuler** à partir de la **modifier** menu (si le focus n’est pas sur le contrôle, le **Annuler** n’est pas disponible).

### <a name="to-edit-properties-for-an-activex-control"></a>Pour modifier les propriétés pour un contrôle ActiveX

Contrôles ActiveX fournis par des fabricants indépendants peuvent sont équipés à leurs propriétés et leurs caractéristiques. Propriétés pour les contrôles ActiveX sont affichées dans le **propriétés** fenêtre. En outre, les pages de propriétés créées par les auteurs du contrôle ActiveX sont affichés dans le **Pages de propriétés** boîte de dialogue (pour afficher le **Page de propriétés** pour un contrôle ActiveX spécifique, cliquez sur le **Page de propriétés** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window)).

Plusieurs onglets s’affichent dans la page de propriétés pour un contrôle ActiveX, selon les feuilles de propriétés qui font partie du contrôle ActiveX.

> [!NOTE]
> La procédure suivante s’applique à l’utilisation de la page de propriétés pour modifier des contrôles ActiveX. Vous pouvez également parcourir et modifier les propriétés ActiveX dans le nouveau **propriétés** fenêtre.

1. Sélectionnez le **ActiveX** contrôle.

1. Sur le **vue** menu, sélectionnez **Page de propriétés** et afficher les propriétés.

1. Apportez les modifications nécessaires dans la page de propriétés.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Pour définir une variable membre pour un contrôle de boîte de dialogue (à l'exception d'un bouton)

Pour définir une variable membre pour un contrôle de boîte de dialogue à l'exception des boutons, vous pouvez utiliser la méthode suivante.

> [!NOTE]
> Ce processus s’applique uniquement aux contrôles de boîte de dialogue dans un projet MFC. Les projets ATL doivent utiliser la **nouveaux Messages Windows et gestionnaires d’événements** boîte de dialogue. Pour plus d’informations, consultez [Message Types associés aux objets d’Interface utilisateur](../mfc/reference/message-types-associated-with-user-interface-objects.md), [modification d’un gestionnaire de Message](../mfc/reference/editing-a-message-handler.md), et [définition d’un gestionnaire de messages pour un Message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. Dans le [éditeur de boîte de dialogue](../windows/dialog-editor.md), sélectionnez un contrôle.

1. Tout en maintenant la **Ctrl** enfoncée, double-cliquez sur le contrôle de boîte de dialogue.

   Le [Assistant Ajout de Variable membre](../ide/add-member-variable-wizard.md) s’affiche.

1. Tapez les informations appropriées dans le **ajouter une Variable membre** Assistant. Pour plus d’informations, consultez [échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md).

1. Sélectionnez **OK** pour revenir à la **boîte de dialogue** éditeur.

   > [!TIP]
   > Pour passer d'un contrôle de boîte de dialogue à son gestionnaire existant, double-cliquez sur le contrôle.

Vous pouvez également utiliser le **Variables membres** onglet dans le [Assistant classe MFC](../mfc/reference/mfc-class-wizard.md) pour ajouter de nouvelles variables de membre pour une classe spécifiée et afficher les variables de membres qui ont déjà été définis.

## <a name="to-delete-a-control"></a>Pour supprimer un contrôle

Dans la boîte de dialogue, sélectionnez le contrôle et appuyez sur la **supprimer** clé.

   \- ou -

Sur le **modifier** menu, sélectionnez **supprimer**.

   > [!TIP]
   > Lors de l’utilisation du **boîte de dialogue** éditeur, dans de nombreux cas, vous pouvez cliquer sur le bouton droit de la souris pour afficher un menu contextuel des commandes fréquemment utilisées.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](controls-in-dialog-boxes.md)<br/>
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->
