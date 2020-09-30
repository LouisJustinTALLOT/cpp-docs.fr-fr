---
title: 'Comment : ajouter, modifier ou supprimer des contrôles (C++)'
ms.date: 02/15/2019
f1_keywords:
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
ms.openlocfilehash: be2923c98ed1b92d4aeb2692591abcaf9f13c5ec
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508832"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Comment : ajouter, modifier ou supprimer des contrôles (C++)

À l’aide de l' **éditeur de boîtes de dialogue**, vous pouvez ajouter, redimensionner, modifier et supprimer des contrôles dans les boîtes de dialogue. Vous pouvez également modifier les propriétés d’un contrôle, telles que son ID, ou bien son affichage initial au moment de l’exécution.

L’onglet **éditeur de boîtes de dialogue** s’affiche dans la [fenêtre boîte à outils](/visualstudio/ide/reference/toolbox) lorsque vous travaillez dans l' **éditeur de boîtes de dialogue**. Vous pouvez également personnaliser la fenêtre **boîte à outils** pour une utilisation plus facile. Pour plus d’informations, consultez [utilisation de la boîte à outils](/visualstudio/ide/using-the-toolbox) et [afficher ou masquer la fenêtre boîte à outils](./dialog-editor.md).

> [!TIP]
> Lorsque vous utilisez l' **éditeur de boîtes de dialogue**, dans de nombreux cas, vous pouvez sélectionner le bouton droit de la souris pour afficher un menu contextuel des commandes fréquemment utilisées.

## <a name="add-controls"></a>ajouter des contrôles

### <a name="to-add-a-control"></a>Pour ajouter un contrôle

1. Assurez-vous que la fenêtre avec onglet de la boîte de dialogue représente le document actif dans le cadre de l’éditeur. Si une boîte de dialogue n’est pas le document actif, vous ne verrez pas l' **onglet Éditeur de boîtes de dialogue** dans la **boîte à outils**.

1. Dans l’onglet **éditeur de boîtes de dialogue** de la fenêtre **boîte à outils** , sélectionnez le contrôle souhaité, puis :

   - Sélectionnez la boîte de dialogue à l’emplacement où vous souhaitez placer le contrôle et le contrôle s’affiche à l’endroit où vous avez sélectionné.

   - Glissez-déplacez le contrôle de la fenêtre **boîte à outils** vers l’emplacement de votre boîte de dialogue. Vous pouvez ensuite déplacer le contrôle ou modifier sa taille et sa forme.

   - Double-cliquez sur le contrôle dans la fenêtre **boîte à outils** et il apparaît dans votre boîte de dialogue. Repositionnez le contrôle à l’emplacement de votre choix.

### <a name="to-add-multiple-controls"></a>Pour ajouter plusieurs contrôles

1. Tout en maintenant la touche **CTRL** enfoncée, sélectionnez un contrôle dans la fenêtre **boîte à outils** .

1. Relâchez la touche **CTRL** et sélectionnez la boîte de dialogue autant de fois que nécessaire pour ajouter le contrôle particulier.

1. Appuyez sur **Échap** pour arrêter de placer des contrôles.

### <a name="to-size-a-control-while-you-add-it"></a>Pour dimensionner un contrôle pendant son ajout

1. Sélectionnez un contrôle dans la fenêtre **boîte à outils** .

1. Placez le curseur sous forme de réticule, où vous souhaitez que l’angle supérieur gauche du nouveau contrôle apparaisse dans votre boîte de dialogue.

1. Sélectionnez et maintenez enfoncé le bouton de la souris pour ancrer l’angle supérieur gauche de votre contrôle dans la boîte de dialogue. Ensuite, faites glisser le curseur vers la droite et vers le dessous, jusqu’à ce que le contrôle ait la taille souhaitée.

   > [!NOTE]
   > Vous pouvez ancrer l’un des quatre coins du contrôle que vous dessinez. Cette procédure utilise l’angle supérieur gauche comme exemple.

1. Relâchez le bouton de la souris. Le contrôle se règle sur la boîte de dialogue dans la taille que vous avez spécifiée.

> [!TIP]
> Vous pouvez redimensionner le contrôle après l’avoir déposé dans la boîte de dialogue en déplaçant les poignées de redimensionnement sur la bordure du contrôle. Pour plus d’informations, consultez [dimensionnement de contrôles individuels](./arrangement-of-controls-on-dialog-boxes.md).

### <a name="to-add-a-custom-control"></a>Pour ajouter un contrôle personnalisé

Vous pouvez ajouter des contrôles personnalisés à la boîte de dialogue. Sélectionnez l’icône de **contrôle personnalisé** dans la **boîte à outils** et faites-la glisser vers votre boîte de dialogue. Pour ajouter un `Syslink` contrôle, ajoutez un contrôle personnalisé, puis affectez à la propriété de **classe** du contrôle la valeur `Syslink` . Cette action entraîne l’actualisation des propriétés et l’affichage des `Syslink` Propriétés de contrôle. Pour plus d’informations sur la classe wrapper MFC, consultez [CLinkCtrl](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Contrôles d’édition

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Pour modifier les propriétés d’un contrôle ou de contrôles

1. Dans la boîte de dialogue, sélectionnez le contrôle que vous souhaitez modifier.

   > [!NOTE]
   > Si vous sélectionnez plusieurs contrôles, seules les propriétés communes aux contrôles sélectionnés peuvent être modifiées.

1. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), modifiez les propriétés de votre contrôle.

   > [!NOTE]
   > Lorsque vous affectez à la propriété **bitmap** d’un bouton, d’une case d’option ou d’un contrôle de case à cocher la **valeur true**, le style BS_BITMAP est implémenté pour votre contrôle. Pour plus d’informations, consultez [styles de bouton](../mfc/reference/styles-used-by-mfc.md#button-styles). Pour obtenir un exemple d’association d’une image bitmap à un contrôle, consultez [CButton :: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Les bitmaps n’apparaissent pas sur votre contrôle tant que vous êtes dans l' **éditeur de boîtes de dialogue**.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Pour annuler les modifications apportées aux propriétés d’un contrôle

1. Assurez-vous que le contrôle a le focus dans l' **éditeur de boîtes de dialogue**.

1. Accédez à menu **modifier**  >  **Annuler**. Si le focus n’est pas sur le contrôle, la commande **Annuler** n’est pas disponible.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Pour définir une variable membre pour un contrôle de boîte de dialogue (à l'exception d'un bouton)

> [!NOTE]
> Ce processus s’applique uniquement aux contrôles de boîte de dialogue dans un projet MFC. Les projets ATL doivent utiliser la boîte de dialogue **nouveaux messages et gestionnaires d’événements Windows** . Pour plus d’informations, consultez [types de messages associés à des objets d’interface utilisateur](../mfc/reference/message-types-associated-with-user-interface-objects.md), [modification d’un gestionnaire de messages](../mfc/reference/editing-a-message-handler.md)et [définition d’un gestionnaire de messages pour un message réfléchi](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. Dans l' [éditeur de boîtes de dialogue](dialog-editor.md), sélectionnez un contrôle.

1. Tout en appuyant sur la touche **CTRL** , double-cliquez sur le contrôle de boîte de dialogue.

   L' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) s’affiche.

1. Tapez les informations appropriées dans l’Assistant **Ajout de variable membre** . Pour plus d’informations, consultez [échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md).

1. Sélectionnez **OK** pour revenir à l' **éditeur de boîtes de dialogue**.

> [!TIP]
> Pour passer d'un contrôle de boîte de dialogue à son gestionnaire existant, double-cliquez sur le contrôle.

Vous pouvez également utiliser l’onglet **variables membres** de l' [Assistant classe MFC](../mfc/reference/mfc-class-wizard.md) pour ajouter de nouvelles variables membres pour une classe spécifiée et afficher les variables membres déjà définies.

## <a name="delete-controls"></a>Supprimer des contrôles

Dans la boîte de dialogue, sélectionnez le contrôle, appuyez sur la touche **Suppr** ou accédez à menu **modifier**  >  **supprimer**.

## <a name="other-issues"></a>Autres problèmes

### <a name="troubleshooting"></a>Résolution des problèmes

Une fois que vous avez ajouté un contrôle commun ou un contrôle RichEdit à une boîte de dialogue, il n’apparaît pas lorsque vous testez la boîte de dialogue. Ou la boîte de dialogue elle-même ne s’affiche pas. Par exemple :

1. Créez un projet Win32, en modifiant les paramètres de l’application pour créer une application Windows (et non une application console).

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), double-cliquez sur le fichier *. RC* .

1. Sous l’option de la boîte de dialogue, double-cliquez sur la boîte de dialogue **à propos** de.

1. Ajoutez un **contrôle d’adresse IP** à la boîte de dialogue.

1. Enregistrer et **régénérer tout**.

1. Exécutez le programme.

1. Dans le menu d' **aide** de la boîte de dialogue, sélectionnez la commande **à propos** de et aucune boîte de dialogue ne s’affiche.

Actuellement, l' **éditeur de boîtes de dialogue** n’ajoute pas automatiquement du code à votre projet lorsque vous faites glisser et déposez les contrôles communs ou RichEdit suivants dans une boîte de dialogue. Visual Studio ne fournit pas non plus d’erreur ou d’avertissement lorsque ce problème se produit. Pour corriger ce problème, ajoutez manuellement le code du contrôle.

:::row:::
   :::column span="":::
      Contrôle d’animation \
      Contrôle personnalisé \
      Sélecteur de date et heure \
      Zone de liste déroulante étendue
   :::column-end:::
   :::column span="":::
      Touche d’accès rapide \
      Contrôle d’adresse IP \
      Contrôle de liste \
      Month Calendar
   :::column-end:::
   :::column span="":::
      Contrôle de progression \
      Contrôle Rich Edit 2,0 \
      Contrôle RichEdit \
      Contrôle Slider
   :::column-end:::
   :::column span="":::
      Contrôle spin \
      Contrôle onglet \
      Contrôle d’arborescence
   :::column-end:::
:::row-end:::

Pour utiliser des contrôles communs dans une boîte de dialogue, vous devez appeler [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) ou `AFXInitCommonControls` avant de créer la boîte de dialogue.

Pour utiliser des contrôles RichEdit, vous devez appeler `LoadLibrary` . Pour plus d’informations, consultez [à propos des contrôles RichEdit](/windows/win32/Controls/about-rich-edit-controls) dans le SDK Windows et [vue d’ensemble du contrôle RichEdit](../mfc/overview-of-the-rich-edit-control.md).

> [!NOTE]
> Pour utiliser un contrôle RichEdit avec MFC, vous devez d’abord appeler [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) pour charger le contrôle RichEdit 2,0 (RICHED20.DLL), ou appeler [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) pour charger l’ancien contrôle RichEdit 1,0 (RICHED32.DLL).
>
> Vous pouvez utiliser la classe actuelle [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) avec l’ancien contrôle RichEdit 1,0, mais `CRichEditCtrl` est conçu uniquement pour prendre en charge le contrôle RichEdit 2,0. Étant donné que RichEdit 1,0 et RichEdit 2,0 sont similaires, la plupart des méthodes fonctionnent. Toutefois, il existe des différences entre les contrôles 1,0 et 2,0, donc certaines méthodes peuvent fonctionner de manière incorrecte ou ne pas fonctionner du tout.

## <a name="insert-activex-controls"></a>Insérer des contrôles ActiveX

Avec Visual Studio, vous pouvez insérer des contrôles ActiveX dans votre boîte de dialogue. Pour plus d’informations, consultez [contrôles ActiveX MFC](../mfc/mfc-activex-controls.md) et [conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md).

La boîte de dialogue **Insérer un contrôle ActiveX** vous permet d’insérer des contrôles ActiveX dans votre boîte de dialogue tout en utilisant l' [éditeur de boîtes de dialogue](dialog-editor.md). Cette boîte de dialogue contient les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Contrôle ActiveX**|Affiche la liste des contrôles ActiveX.<br/><br/>L’insertion d’un contrôle à partir de cette boîte de dialogue ne génère pas de classe wrapper. Si vous avez besoin d’une classe wrapper, utilisez [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) pour en créer une, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md).<br/><br/>Si un contrôle ActiveX n’apparaît pas dans cette boîte de dialogue, essayez d’installer le contrôle conformément aux instructions du fournisseur.|
|**Chemin d’accès**|Affiche le fichier dans lequel le contrôle ActiveX est trouvé.|

> [!CAUTION]
> Il se peut que la distribution de tous les contrôles ActiveX sur votre système ne soit pas autorisée juridiquement. Reportez-vous au contrat de licence du logiciel qui a installé les contrôles ou contactez l’éditeur du logiciel.

### <a name="to-add-an-activex-control"></a>Pour ajouter un contrôle ActiveX

1. Ouvrez une boîte de dialogue dans l' **éditeur de boîtes de dialogue**.

1. Cliquez avec le bouton droit n’importe où dans le corps de la boîte de dialogue, puis sélectionnez **Insérer un contrôle ActiveX**.

   La boîte de dialogue **Insérer un contrôle ActiveX** apparaît et affiche tous les contrôles ActiveX sur votre système. En bas de la boîte de dialogue figure le chemin d’accès au fichier de contrôle ActiveX.

1. Sélectionnez le contrôle que vous souhaitez ajouter à votre boîte de dialogue, puis choisissez **OK**.

   Le contrôle apparaît dans la boîte de dialogue, où vous pouvez le modifier ou créer des gestionnaires comme vous le feriez pour n’importe quel autre contrôle.

> [!TIP]
> Vous pouvez utiliser le menu contextuel de l' **éditeur de boîtes de dialogue** pour ajouter rapidement des contrôles ActiveX inscrits à une boîte de dialogue ou essayer d’ajouter des contrôles ActiveX à la fenêtre **boîte à outils** pour y accéder facilement.

### <a name="to-edit-properties-for-an-activex-control"></a>Pour modifier les propriétés d’un contrôle ActiveX

Les contrôles ActiveX fournis par des fournisseurs indépendants peuvent être dotés de leurs propres propriétés et caractéristiques. Ces propriétés sont affichées dans la fenêtre **Propriétés** . Toutes les pages de propriétés créées par les enregistreurs du contrôle ActiveX s’affichent dans la boîte de dialogue **pages de propriétés** . (Pour afficher la **page de propriétés** d’un contrôle ActiveX spécifique, sélectionnez le bouton **page de propriétés** dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window)).

- Sélectionnez le contrôle **ActiveX** et accédez à **View**  >  la page de**Propriétés** de la vue de menu pour afficher les propriétés. Apportez les modifications nécessaires dans la page de propriétés.

   Différents onglets s’affichent dans la page de propriétés d’un contrôle ActiveX, selon les feuilles de propriétés qui font partie du contrôle ActiveX.

> [!NOTE]
> Cette procédure s’applique à l’utilisation de la page de propriétés pour modifier les contrôles ActiveX. Vous pouvez également parcourir et modifier les propriétés ActiveX dans la nouvelle fenêtre **Propriétés** .

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Gérer les contrôles de boîte de dialogue](controls-in-dialog-boxes.md)<br/>
[Comment : mettre en page des contrôles](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Comment : définir l’accès aux contrôles et les valeurs](defining-mnemonics-access-keys.md)

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
