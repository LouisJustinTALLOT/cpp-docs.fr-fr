---
title: 'Procédure : Ajouter, modifier, ou supprimer des contrôles (C++)'
ms.date: 02/15/2019
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
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: 2e3e671cd92313ad120d2cd6aae3f7e815e09e65
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025362"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Procédure : Ajouter, modifier, ou supprimer des contrôles (C++)

À l’aide de la **boîte de dialogue Éditeur**, vous pouvez ajouter, redimensionner, modifier et supprimer des contrôles dans les boîtes de dialogue. Vous pouvez également modifier les propriétés d’un contrôle, telles que son ID, ou s’il est visible initialement en cours d’exécution.

Le **boîte de dialogue Éditeur** onglet s’affiche dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox) lorsque vous travaillez dans le **boîte de dialogue Éditeur**. Vous pouvez également personnaliser le **boîte à outils** fenêtre pour faciliter son utilisation. Pour plus d’informations, consultez [à l’aide de la boîte à outils](/visualstudio/ide/using-the-toolbox) et [afficher ou masquer la fenêtre Boîte à outils](showing-or-hiding-the-dialog-editor-toolbar.md).

> [!TIP]
> Lors de l’utilisation du **boîte de dialogue Éditeur**, dans de nombreux cas, vous pouvez sélectionner le bouton droit de la souris pour afficher un menu contextuel des commandes fréquemment utilisées.

## <a name="add-controls"></a>Ajouter des contrôles

### <a name="to-add-a-control"></a>Pour ajouter un contrôle

1. Assurez-vous que la fenêtre avec onglet de la boîte de dialogue représente le document actif dans le cadre de l’éditeur. Si une boîte de dialogue n’est pas le document actif, vous ne voyez pas le **onglet de boîte de dialogue Éditeur** dans le **boîte à outils**.

1. Sur le **boîte de dialogue Éditeur** onglet de la **boîte à outils** fenêtre, sélectionnez le contrôle souhaité, puis :

   - Sélectionnez la boîte de dialogue à l’emplacement où vous souhaitez placer le contrôle et le contrôle s’affiche où vous avez sélectionné.

   - Faites glisser le contrôle à partir de la **boîte à outils** fenêtre à l’emplacement sur votre boîte de dialogue et vous pouvez ensuite déplacer les contrôles ou modifier leur taille et la forme.

   - Double-cliquez sur le contrôle dans le **boîte à outils** fenêtre et apparaît dans votre boîte de dialogue, puis repositionnez le contrôle à l’emplacement de votre choix.

### <a name="to-add-multiple-controls"></a>Pour ajouter plusieurs contrôles

1. Tout en maintenant enfoncée la **Ctrl** enfoncée, sélectionnez un contrôle dans le **boîte à outils** fenêtre.

1. Mise en production la **Ctrl** la clé, sélectionnez la boîte de dialogue autant de fois que vous souhaitez ajouter ce contrôle.

1. Appuyez sur **ÉCHAP** pour arrêter.

### <a name="to-size-a-control-while-you-add-it"></a>Pour dimensionner un contrôle pendant son ajout

1. Sélectionnez un contrôle dans le **boîte à outils** fenêtre.

1. Placez votre curseur qui s’affiche sous forme de croix, où vous souhaitez le coin supérieur gauche du nouveau contrôle doivent se trouver sur votre boîte de dialogue.

1. Sélectionnez et maintenez le bouton de la souris pour ancrer le coin supérieur gauche de votre contrôle sur la boîte de dialogue, puis faites glisser le curseur vers la droite et vers le bas jusqu'à ce que le contrôle est la taille voulue.

   > [!NOTE]
   > Vous pouvez ancrer un des quatre coins du contrôle que vous dessinez. Cette procédure utilisé le coin supérieur gauche comme exemple.

1. Relâchez le bouton de la souris. Le contrôle est placé dans la boîte de dialogue dans la taille spécifiée.

> [!TIP]
> Vous pouvez redimensionner le contrôle après le déposant sur la boîte de dialogue en déplaçant les poignées de redimensionnement sur la bordure du contrôle. Pour plus d’informations, consultez [dimensionnement de contrôles individuels](../windows/sizing-individual-controls.md).

### <a name="to-add-a-custom-control"></a>Pour ajouter un contrôle personnalisé

Vous pouvez ajouter des contrôles personnalisés à la boîte de dialogue en sélectionnant le **contrôle personnalisé** icône dans le **boîte à outils** et faites-la glisser vers votre boîte de dialogue. Pour ajouter un **Syslink** contrôler, ajoutez un contrôle personnalisé, puis modifier le contrôle **classe** propriété **Syslink**. Cette action entraîne les propriétés actualiser et afficher le **Syslink** propriétés du contrôle. Pour plus d’informations sur la classe wrapper MFC, consultez [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Contrôles d’édition

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Pour modifier les propriétés d’un contrôle ou de contrôles

1. Dans la boîte de dialogue, sélectionnez le contrôle que vous souhaitez modifier.

   > [!NOTE]
   > Si vous sélectionnez plusieurs contrôles, uniquement les propriétés communes aux contrôles sélectionnés peuvent être modifiées.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), modifier les propriétés de votre contrôle.

   > [!NOTE]
   > Lorsque vous définissez la **Bitmap** propriété pour un bouton, une case d’option ou un contrôle de case à cocher égal à **True**, le style BS_BITMAP est implémenté pour votre contrôle. Pour plus d’informations, consultez [Styles de boutons](../mfc/reference/styles-used-by-mfc.md#button-styles). Pour obtenir un exemple d’association d’une image bitmap à un contrôle, consultez [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Bitmaps n’apparaissent pas sur votre contrôle pendant que vous êtes dans le **boîte de dialogue Éditeur**.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Pour annuler les modifications apportées aux propriétés d’un contrôle

1. Assurez-vous que le contrôle a le focus dans le **boîte de dialogue Éditeur**.

1. Accédez au menu **modifier** > **Annuler**. Si le focus n’est pas sur le contrôle, le **Annuler** n’est pas disponible.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Pour définir une variable membre pour un contrôle de boîte de dialogue (à l'exception d'un bouton)

> [!NOTE]
> Ce processus s’applique uniquement aux contrôles de boîte de dialogue dans un projet MFC. Les projets ATL doivent utiliser la **nouveaux Messages Windows et gestionnaires d’événements** boîte de dialogue. Pour plus d’informations, consultez [Message Types associés aux objets d’Interface utilisateur](../mfc/reference/message-types-associated-with-user-interface-objects.md), [modification d’un gestionnaire de Message](../mfc/reference/editing-a-message-handler.md), et [définition d’un gestionnaire de messages pour un Message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. Dans le [boîte de dialogue Éditeur](../windows/dialog-editor.md), sélectionnez un contrôle.

1. Tout en maintenant la **Ctrl** enfoncée, double-cliquez sur le contrôle de boîte de dialogue.

   Le [Assistant Ajout de Variable membre](../ide/add-member-variable-wizard.md) s’affiche.

1. Tapez les informations appropriées dans le **ajouter une Variable membre** Assistant. Pour plus d’informations, consultez [échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md).

1. Sélectionnez **OK** pour revenir à la **boîte de dialogue Éditeur**.

> [!TIP]
> Pour passer d'un contrôle de boîte de dialogue à son gestionnaire existant, double-cliquez sur le contrôle.

Vous pouvez également utiliser le **Variables membres** onglet dans le [Assistant classe MFC](../mfc/reference/mfc-class-wizard.md) pour ajouter de nouvelles variables de membre pour une classe spécifiée et afficher les variables de membres qui ont déjà été définis.

## <a name="delete-controls"></a>Supprimer des contrôles

Dans la boîte de dialogue, sélectionnez le contrôle, puis appuyez sur la **supprimer** clé, ou accédez au menu **modifier** > **supprimer**.

## <a name="other-issues"></a>Autres problèmes

### <a name="troubleshooting"></a>Résolution des problèmes

Après avoir ajouté un contrôle commun ou un contrôle RichEdit une boîte de dialogue, elle ne s’affiche lorsque vous testez la boîte de dialogue ou de la boîte de dialogue n’apparaît, par exemple :

1. Créez un projet Win32, en modifiant les paramètres d’application pour créer une application Windows (pas une application console).

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), double-cliquez sur le *.rc* fichier.

1. Sous l’option de la boîte de dialogue, double-cliquez sur le **sur** boîte.

1. Ajouter un **contrôle d’adresse IP** à la boîte de dialogue.

1. Enregistrer et **régénérer tout**.

1. Exécutez le programme.

1. Dans la boîte de dialogue **aide** menu, sélectionnez le **sur** commande et observer aucune boîte de dialogue ne s’affiche.

Actuellement, le **boîte de dialogue Éditeur** n’ajoute pas automatiquement code à votre projet lorsque vous faites glisser et déposez les contrôles communs ou RichEdit dans une boîte de dialogue. Ni Visual Studio fournit-il une erreur ou un avertissement lorsque ce problème se produit. Pour résoudre le problème, ajoutez manuellement le code pour le contrôle.

||||
|-|-|-|
|Contrôle Slider|Contrôle d’arborescence|Date Time Picker|
|Contrôle Spin|Contrôle onglet|Calendrier mensuel|
|Contrôle de progression|Contrôle Animation|Contrôle d’adresse IP|
|Touche d’accès rapide|Contrôle RichEdit|Zone de liste déroulante étendue|
|Contrôle de liste|Contrôle Rich Edit 2.0|Contrôle personnalisé|

Pour utiliser les contrôles communs dans une boîte de dialogue, vous devez appeler [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) ou `AFXInitCommonControls` avant de créer la boîte de dialogue.

Pour utiliser les contrôles RichEdit, vous devez appeler `LoadLibrary`. Pour plus d’informations, consultez [sur les contrôles RichEdit](/windows/desktop/Controls/about-rich-edit-controls) dans le SDK Windows et [vue d’ensemble du contrôle RichEdit](../mfc/overview-of-the-rich-edit-control.md).

> [!NOTE]
> Pour utiliser un contrôle RichEdit avec MFC, vous devez d’abord appeler [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) pour charger le contrôle RichEdit 2.0 (RICHED20. DLL), ou appelez [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) pour charger l’ancien contrôle RichEdit 1.0 (Riched32). (DLL).
>
> Vous pouvez utiliser actuel [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) classe avec l’ancien contrôle RichEdit 1.0, mais `CRichEditCtrl` est conçu uniquement pour prendre en charge le contrôle RichEdit 2.0. RichEdit 1.0 et RichEdit 2.0 étant similaires, la plupart des méthodes fonctionnera. Toutefois, il existe certaines différences entre les contrôles 1.0 et 2.0, et certaines méthodes peuvent fonctionner de manière incorrecte ou ne fonctionne pas du tout.

### <a name="activex-controls"></a>Contrôles ActiveX

Avec Visual Studio, vous pouvez insérer des contrôles ActiveX dans votre boîte de dialogue. Pour plus d’informations, consultez [contrôles ActiveX MFC](../mfc/mfc-activex-controls.md) et [conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md).

Le **insérer un contrôle ActiveX** boîte de dialogue permet d’insérer des contrôles ActiveX dans votre boîte de dialogue lors de l’utilisation du [boîte de dialogue Éditeur](../windows/dialog-editor.md). Cette boîte de dialogue contient les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Contrôle ActiveX**|Affiche une liste des contrôles ActiveX.<br/><br/>Insertion d’un contrôle à partir de cette boîte de dialogue ne génère pas une classe wrapper. Si vous avez besoin d’une classe wrapper, utilisez [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) pour en créer un, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md).<br/><br/>Si un contrôle ActiveX n’apparaît pas dans cette boîte de dialogue, essayez d’installer le contrôle selon les instructions du fournisseur.|
|**Chemin d’accès**|Affiche le fichier dans lequel le contrôle ActiveX est trouvé.|

> [!CAUTION]
> Il se peut que la distribution de tous les contrôles ActiveX sur votre système ne soit pas autorisée juridiquement. Reportez-vous au contrat de licence du logiciel qui a installé les contrôles ou contactez l’éditeur du logiciel.

#### <a name="to-add-an-activex-control"></a>Pour ajouter un contrôle ActiveX

1. Ouvrir une boîte de dialogue le **boîte de dialogue Éditeur**.

1. Avec le bouton droit n’importe où dans le corps de la boîte de dialogue et sélectionnez **insérer un contrôle ActiveX**.

   Le **insérer un contrôle ActiveX** boîte de dialogue apparaît, affichant tous les contrôles ActiveX sur votre système. En bas de la boîte de dialogue figure le chemin d’accès au fichier de contrôle ActiveX.

1. Sélectionnez le contrôle que vous souhaitez ajouter à votre boîte de dialogue et sélectionnez **OK**.

   Le contrôle apparaît dans la boîte de dialogue, où vous pouvez le modifier ou créer des gestionnaires comme vous le feriez pour n’importe quel autre contrôle.

> [!TIP]
> Vous pouvez utiliser le menu contextuel dans le **boîte de dialogue Éditeur** pour rapidement ajouter des contrôles ActiveX inscrits à une boîte de dialogue, ou essayez d’ajouter des contrôles ActiveX les **boîte à outils** fenêtre pour pouvoir accéder facilement.

#### <a name="to-edit-properties-for-an-activex-control"></a>Pour modifier les propriétés pour un contrôle ActiveX

Contrôles ActiveX fournis par des fabricants indépendants peuvent sont équipés à leurs propriétés et leurs caractéristiques. Ces propriétés sont affichées dans le **propriétés** fenêtre, y compris toute propriété pages créées par les auteurs du contrôle ActiveX sont affichées dans le **Pages de propriétés** (permet d’afficher le  **Page de propriétés** pour un contrôle ActiveX spécifique, sélectionnez le **Page de propriétés** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window)).

- Sélectionnez le **ActiveX** contrôler et accédez au menu **vue** > **Page de propriétés** pour afficher les propriétés. Apportez les modifications nécessaires dans la page de propriétés.

   Plusieurs onglets s’affichent dans la page de propriétés pour un contrôle ActiveX, selon les feuilles de propriétés qui font partie du contrôle ActiveX.

> [!NOTE]
> Cette procédure s’applique à l’utilisation de la page de propriétés pour modifier des contrôles ActiveX. Vous pouvez également parcourir et modifier les propriétés ActiveX dans le nouveau **propriétés** fenêtre.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Gérer les contrôles de boîte de dialogue](controls-in-dialog-boxes.md)<br/>
[Guide pratique pour disposer les contrôles](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Guide pratique pour définir les valeurs et l’accès au contrôle](defining-mnemonics-access-keys.md)<br/>

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