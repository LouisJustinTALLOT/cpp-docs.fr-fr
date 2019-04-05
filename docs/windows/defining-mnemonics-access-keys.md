---
title: 'Procédure : Définir le contrôle d’accès et des valeurs (C++)'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: c49913597f51ef231073b89d60ad9718b1113f44
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041482"
---
# <a name="how-to-define-control-access-and-values-c"></a>Procédure : Définir le contrôle d’accès et des valeurs (C++)

## <a name="tab-order"></a>Ordre de tabulation

L’ordre de tabulation est l’ordre dans lequel le **onglet** touche déplace le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue. Généralement, l’ordre de tabulation se déroule de gauche à droite et de haut en bas dans une boîte de dialogue. Chaque contrôle possède une **Tabstop** propriété qui détermine si un contrôle reçoit le focus d’entrée.

- Pour définir le focus d’entrée pour un contrôle, dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez **True** ou **False** dans le **Tabstop** propriété.

Même les contrôles qui n’ont pas la **Tabstop** propriété définie sur **True** doivent faire partie de l’ordre de tabulation, en particulier pour les contrôles qui n’ont pas des légendes. Texte statique qui contient une clé d’accès pour un contrôle lié doit précéder immédiatement le contrôle concerné dans l’ordre de tabulation.

> [!NOTE]
> Si votre boîte de dialogue contient des contrôles qui se chevauchent, la modification de l’ordre de tabulation peut changer la façon des que contrôles sont affichés. Contrôles fournis plus loin dans l’ordre de tabulation sont toujours affichés au-dessus des contrôles superposés qui les précèdent dans l’ordre de tabulation.

- Pour afficher l’ordre de tabulation actuel pour tous les contrôles, accédez au menu **Format** > **l’ordre de tabulation**, ou appuyez sur **Ctrl** + **D**.

   Un nombre dans le coin supérieur gauche de chaque contrôle affiche sa place dans l’ordre de tabulation en cours.

- Pour modifier l’ordre de tabulation pour tous les contrôles, accédez au menu **Format** > **l’ordre de tabulation** et définir l’ordre de tabulation en sélectionnant chaque contrôle dans l’ordre que vous souhaitez que le **onglet** clé à suivre.

- Pour modifier l’ordre de tabulation pour deux ou plusieurs contrôles, accédez au menu **Format** > **l’ordre de tabulation**. Maintenez la **Ctrl** la clé, sélectionnez le contrôle où le changement dans l’ordre commencer, puis relâchez le **Ctrl** la clé, sélectionnez les contrôles dans l’ordre souhaité le **onglet** clé pour Suivez à partir de ce point.

   Par exemple, si vous souhaitez modifier l’ordre des contrôles `7` via `9`, maintenez la touche **Ctrl**, puis sélectionnez le contrôle `6` première.

- Pour affecter à un contrôle spécifique numéro `1`, ou tout d’abord dans l’ordre de tabulation, double-cliquez sur le contrôle.

> [!TIP]
> Une fois que vous entrez **l’ordre de tabulation** mode, appuyez sur **ÉCHAP** ou **entrée** pour quitter **l’ordre de tabulation** mode et désactiver la possibilité de modifier l’ordre de tabulation.

## <a name="mnemonics-access-keys"></a>Mnémoniques (touches d’accès rapide)

En règle générale, les utilisateurs du clavier déplacent le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue avec le **onglet** et **flèche** clés. Toutefois, vous pouvez définir une clé d’accès (un nom mnémonique ou facile à mémoriser) qui permet aux utilisateurs de choisir un contrôle en appuyant sur une clé unique.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Pour définir une clé d’accès pour un contrôle avec une légende visible (boutons de commande, cases à cocher et des boutons radio)

1. Sélectionnez le contrôle dans la boîte de dialogue.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), dans le **légende** propriété, tapez un nouveau nom pour le contrôle en tapant une esperluette (`&`) devant la lettre que vous souhaitez comme touche d’accès pour ce contrôle. Par exemple, `&Radio1`.

1. Appuyez sur **Entrée**.

   Un trait de soulignement apparaît dans la légende pour indiquer la clé d’accès, par exemple, **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Pour définir une clé d’accès pour un contrôle sans légende visible

1. Créez une légende pour le contrôle à l’aide un **texte statique** dans contrôler le [boîte à outils](/visualstudio/ide/reference/toolbox).

1. Dans la légende de texte statique, tapez une esperluette (`&`) devant la lettre que vous souhaitez comme touche d’accès.

1. Assurez-vous que le contrôle de texte statique précède immédiatement le contrôle qu’il identifie dans l’ordre de tabulation.

> [!NOTE]
> Toutes les clés d’accès au sein d’une boîte de dialogue doivent être uniques. Pour vérifier les clés d’accès en double, accédez au menu **Format** > **vérifier les mnémoniques**.

## <a name="combo-box-values"></a>Valeurs de zone de liste déroulante

Vous pouvez ajouter des valeurs à un contrôle combo box tant que vous avez le **boîte de dialogue Éditeur** ouvrir.

> [!TIP]
> Il est judicieux d’ajouter toutes les valeurs à la zone de liste déroulante *avant* dimensionner la zone dans le **boîte de dialogue Éditeur**, ou vous pouvez tronquer le texte qui doit apparaître dans le contrôle de liste déroulante.

### <a name="to-enter-values-into-a-combo-box-control"></a>Pour entrer des valeurs dans un contrôle combo box

1. Choisissez la liste déroulante contrôle de zone en le sélectionnant.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), faites défiler jusqu'à la **données** propriété.

   > [!NOTE]
   > Si vous affichez les propriétés regroupées par type, **données** s’affiche dans le **divers** propriétés.

1. Sélectionnez la zone de valeur pour le **données** propriété et tapez vos valeurs de données, séparées par des points-virgules.

   > [!NOTE]
   > Ne placez pas les espaces entre les valeurs car ils interfèrent avec le tri alphabétique dans la liste déroulante.

1. Appuyez sur **entrée** lorsque vous avez terminé d’ajouter des valeurs.

Pour plus d’informations sur l’agrandissement de la partie déroulante d’une zone de liste déroulante, consultez [définition de la taille de la zone de liste déroulante et de sa liste de déroulante](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Vous ne pouvez pas ajouter des valeurs à des projets Win32 à l’aide de cette procédure (le **données** propriété apparaît en grisé pour les projets Win32). Car les projets Win32 n’ont pas de bibliothèques qui ajoutent cette fonctionnalité, vous devez ajouter par programmation des valeurs à une zone de liste déroulante avec un projet Win32.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Pour tester l’apparence des valeurs dans une zone de liste déroulante

1. Après avoir entré les valeurs dans le **données** propriété, sélectionnez le **Test** bouton sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

1. Faites défiler vers le bas la liste de valeur entière. Les valeurs s’affichent exactement comme ils sont tapés dans le **données** propriété dans le **propriétés** fenêtre. Il n’existe aucune orthographe ou la vérification de la mise en majuscules.

1. Appuyez sur **ÉCHAP** pour revenir à la **boîte de dialogue** éditeur.

## <a name="radio-button-values"></a>Valeurs de la case d’option

Lorsque vous ajoutez des cases d’option à une boîte de dialogue, traitez-les comme un groupe en définissant un **groupe** propriété dans le **propriétés** fenêtre pour le premier bouton dans le groupe. Un ID de contrôle pour cette case d’option apparaît alors dans [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md), ce qui vous permet d’ajouter une variable membre pour le groupe de cases d’option.

Vous pouvez avoir plusieurs groupes de cases d’option sur une boîte de dialogue. Ajoutez chaque groupe à l’aide de la procédure suivante.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Pour ajouter un groupe de cases d’option à une boîte de dialogue

1. Sélectionnez le contrôle de case d’option dans le [fenêtre Boîte à outils](/visualstudio/ide/reference/toolbox) et choisissez l’emplacement dans la boîte de dialogue où placer le contrôle.

1. Répétez l’étape ci-dessus pour ajouter des boutons radio autant que nécessaire. Assurez-vous que les cases d’option dans le groupe sont suivent dans l’ordre de tabulation.

1. Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), affectez la valeur **True** à la propriété *Groupe* de la **première**case d’option dans l’ordre de tabulation.

   Modification de la **groupe** propriété **True** ajoute le style WS_GROUP à l’entrée du bouton dans l’objet de la boîte de dialogue du script de ressources et empêche que l’utilisateur peut sélectionner plus d’une case d’option à la fois dans le groupe (si l’utilisateur sélectionne une case, les autres dans le groupe est désactivée).

   > [!NOTE]
   > La propriété **Groupe** de la première case d’option du groupe doit avoir la valeur **True**. Si vous avez d’autres contrôles qui ne font pas partie du groupe de cases, définissez le **groupe** propriété du premier contrôle *qui est en dehors du groupe* à **True** également. Vous pouvez rapidement identifier le premier contrôle en dehors du groupe à l’aide de **Ctrl**+**D** pour afficher l’ordre de tabulation.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Pour ajouter une variable membre pour le groupe de cases d’option

1. Cliquez sur le premier contrôle de bouton de case d’option dans l’ordre de tabulation (le contrôle dominant et celui dont le **groupe** propriété définie sur **True**) et choisissez **ajouter une Variable**.

1. Dans l’ [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md), cochez la case **Variable de contrôle** , puis sélectionnez la case d’option **Valeur** .

   - Dans la zone **Nom de la variable** , tapez un nom pour la nouvelle variable membre.

   - Dans la zone de liste **Type de variable** , sélectionnez **int** ou tapez *int*.

   Vous pouvez maintenant modifier votre code pour spécifier la case d’option qui doit apparaître sélectionnée. Par exemple, `m_radioBox1 = 0;` sélectionne le premier bouton de case d’option dans le groupe.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Gérer les contrôles de boîte de dialogue](controls-in-dialog-boxes.md)<br/>
[Procédure : Ajouter, modifier, ou supprimer des contrôles](adding-editing-or-deleting-controls.md)<br/>
[Procédure : Contrôles de disposition](arrangement-of-controls-on-dialog-boxes.md)<br/>