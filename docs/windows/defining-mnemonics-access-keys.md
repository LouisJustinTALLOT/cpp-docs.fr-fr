---
title: 'Comment : définir l’accès aux contrôles et lesC++valeurs ()'
ms.date: 02/15/2019
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
ms.openlocfilehash: 8ebd8d48b68581bf00215b4ca14f5ac0a543a3c0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443899"
---
# <a name="how-to-define-control-access-and-values-c"></a>Comment : définir l’accès aux contrôles et lesC++valeurs ()

## <a name="tab-order"></a>Ordre de tabulation

L’ordre de tabulation est l’ordre dans lequel la touche **Tab** déplace le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue. En général, l’ordre de tabulation se poursuit de gauche à droite et de haut en bas dans une boîte de dialogue. Chaque contrôle possède une propriété **TabStop** qui détermine si un contrôle reçoit le focus d’entrée.

- Pour définir le focus d’entrée pour un contrôle, dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez **true** ou **false** dans la propriété **TabStop** .

Même les contrôles dont la propriété **TabStop** n’a pas la valeur **true** doivent faire partie de l’ordre de tabulation, en particulier pour les contrôles qui n’ont pas de légende. Le texte statique qui contient une touche d’accès pour un contrôle associé doit précéder immédiatement le contrôle associé dans l’ordre de tabulation.

> [!NOTE]
> Si votre boîte de dialogue contient des contrôles qui se chevauchent, la modification de l’ordre de tabulation peut modifier le mode d’affichage des contrôles. Les contrôles qui arrivent plus tard dans l’ordre de tabulation sont toujours affichés en plus des contrôles qui se chevauchent qui les précèdent dans l’ordre de tabulation.

- Pour afficher l’ordre de tabulation actuel pour tous les contrôles, accédez au menu **Format** > **ordre de tabulation**, ou appuyez sur **CTRL** + **D**.

   Un nombre situé dans le coin supérieur gauche de chaque contrôle montre son emplacement dans l’ordre de tabulation actuel.

- Pour modifier l’ordre de tabulation pour tous les contrôles, accédez à menu **Format** > **ordre de tabulation** et définissez l’ordre de tabulation en sélectionnant chaque contrôle dans l’ordre de la touche **Tab** .

- Pour modifier l’ordre de tabulation d’au moins deux contrôles, accédez à menu **Format** > **ordre de tabulation**. Maintenez la touche **CTRL** enfoncée et sélectionnez le contrôle où commencera la modification, puis relâchez la touche **CTRL** et sélectionnez les contrôles dans l’ordre dans lequel vous souhaitez que la touche **Tab** suive à partir de ce point.

   Par exemple, si vous souhaitez modifier l’ordre des contrôles `7` via `9`, maintenez la **touche Ctrl**enfoncée, puis sélectionnez contrôle `6` d’abord.

- Pour définir un contrôle spécifique sur le nombre `1`ou d’abord dans l’ordre de tabulation, double-cliquez sur le contrôle.

> [!TIP]
> Une fois que vous avez entré le mode d' **ordre de tabulation** , appuyez sur **Échap** ou sur **entrée** pour quitter le mode d' **ordre de tabulation** et désactiver la possibilité de modifier l’ordre de tabulation.

## <a name="mnemonics-access-keys"></a>Mnémoniques (touches d’accès)

Normalement, les utilisateurs du clavier déplacent le focus d’entrée d’un contrôle à un autre dans une boîte de dialogue avec les touches de **direction** et de **tabulation** . Toutefois, vous pouvez définir une touche d’accès rapide (un nom mnémonique ou facile à mémoriser) qui permet aux utilisateurs de choisir un contrôle en appuyant sur une seule touche.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Pour définir une touche d’accès pour un contrôle à l’aide d’une légende visible (boutons de commande, cases à cocher et cases d’option)

1. Sélectionnez le contrôle dans la boîte de dialogue.

1. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), dans la propriété **légende** , tapez un nouveau nom pour le contrôle, en tapant une esperluette (`&`) devant la lettre que vous souhaitez comme clé d’accès pour ce contrôle. Par exemple : `&Radio1`.

1. Appuyez sur **Entrée**.

   Un trait de soulignement apparaît dans la légende affichée pour indiquer la touche d’accès, par exemple **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Pour définir une touche d’accès pour un contrôle sans légende visible

1. Créez une légende pour le contrôle à l’aide d’un contrôle de **texte statique** dans la [boîte à outils](/visualstudio/ide/reference/toolbox).

1. Dans la légende de texte statique, tapez une esperluette (`&`) devant la lettre que vous souhaitez comme clé d’accès.

1. Assurez-vous que le contrôle de texte statique précède immédiatement le contrôle qu’il étiquette dans l’ordre de tabulation.

> [!NOTE]
> Toutes les touches d’accès au sein d’une boîte de dialogue doivent être uniques. Pour rechercher les clés d’accès en double, accédez au menu **Format** > **vérifier les mnémoniques**.

## <a name="combo-box-values"></a>Valeurs de zone de liste déroulante

Vous pouvez ajouter des valeurs à un contrôle zone de liste déroulante tant que l' **éditeur de boîtes de dialogue** est ouvert.

> [!TIP]
> Il est judicieux d’ajouter toutes les valeurs à la zone de liste déroulante *avant* de dimensionner la zone dans l' **éditeur de boîtes de dialogue**, ou vous pouvez tronquer le texte qui doit apparaître dans le contrôle de liste déroulante.

### <a name="to-enter-values-into-a-combo-box-control"></a>Pour entrer des valeurs dans un contrôle de zone de liste déroulante

1. Sélectionnez le contrôle de zone de liste déroulante en le sélectionnant.

1. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), faites défiler jusqu’à la propriété **données** .

   > [!NOTE]
   > Si vous affichez les propriétés regroupées par type, les **données** s’affichent dans les propriétés **diverses** .

1. Sélectionnez la zone valeur pour la propriété **données** et tapez vos valeurs de données, séparées par des points-virgules.

   > [!NOTE]
   > Ne placez pas d’espace entre les valeurs, car les espaces interfèrent avec l’ordre alphabétique dans la liste déroulante.

1. Appuyez sur **entrée** lorsque vous avez fini d’ajouter des valeurs.

Pour plus d’informations sur l’agrandissement de la partie déroulante d’une zone de liste déroulante, consultez [définition de la taille de la zone de liste déroulante et de sa liste déroulante](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Vous ne pouvez pas ajouter de valeurs aux projets Win32 à l’aide de cette procédure (la propriété de **données** est grisée pour les projets Win32). Étant donné que les projets Win32 n’ont pas de bibliothèques qui ajoutent cette fonctionnalité, vous devez ajouter par programme des valeurs à une zone de liste déroulante avec un projet Win32.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Pour tester l’apparence des valeurs dans une zone de liste déroulante

1. Après avoir entré les valeurs dans la propriété **données** , sélectionnez le bouton **test** dans la [barre d’outils](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)de l’éditeur de boîtes de dialogue.

1. Essayez de faire défiler la liste des valeurs entières. Les valeurs apparaissent exactement telles qu’elles sont tapées dans la propriété **données** de la fenêtre **Propriétés** . Il n’y a aucune vérification de l’orthographe ou de la casse.

1. Appuyez sur **Échap** pour revenir à l’éditeur de **boîte de dialogue** .

## <a name="radio-button-values"></a>Valeurs des cases d’option

Lorsque vous ajoutez des cases d’option à une boîte de dialogue, traitez-les comme un groupe en définissant une propriété de **groupe** dans la fenêtre **Propriétés** du premier bouton du groupe. Un ID de contrôle pour cette case d’option apparaît alors dans [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md), ce qui vous permet d’ajouter une variable membre pour le groupe de cases d’option.

Vous pouvez avoir plusieurs groupes de cases d’option dans une boîte de dialogue. Ajoutez chaque groupe à l’aide de la procédure suivante.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Pour ajouter un groupe de cases d’option à une boîte de dialogue

1. Sélectionnez le contrôle de case d’option dans la [fenêtre boîte à outils](/visualstudio/ide/reference/toolbox) et choisissez l’emplacement dans la boîte de dialogue où placer le contrôle.

1. Répétez l’étape ci-dessus pour ajouter autant de cases d’option que vous le souhaitez. Assurez-vous que les cases d’option du groupe se suivent dans l’ordre de tabulation.

1. Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), affectez la valeur **True** à la propriété *Groupe* de la **première**case d’option dans l’ordre de tabulation.

   La modification de la propriété de **groupe** en **true** ajoute le style de WS_GROUP à l’entrée du bouton dans l’objet de boîte de dialogue du script de ressources et empêche l’utilisateur de sélectionner plusieurs cases d’option à la fois dans le groupe de boutons (si l’utilisateur sélectionne une case d’option, les autres cases à cocher sont désactivées).

   > [!NOTE]
   > La propriété **Groupe** de la première case d’option du groupe doit avoir la valeur **True**. Si vous avez d’autres contrôles qui ne font pas partie du groupe de boutons, affectez également la valeur **true** à la propriété **Group** du premier contrôle *qui est en dehors du groupe* . Vous pouvez rapidement identifier le premier contrôle en dehors du groupe en utilisant **Ctrl**+**D** pour afficher l’ordre de tabulation.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Pour ajouter une variable membre pour le groupe de cases d’option

1. Cliquez avec le bouton droit sur le premier contrôle de case d’option dans l’ordre de tabulation (le contrôle dominant et celui dont la propriété **Group** a la valeur **true**), puis choisissez **Ajouter une variable**.

1. Dans l’ [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md), cochez la case **Variable de contrôle** , puis sélectionnez la case d’option **Valeur** .

   - Dans la zone **Nom de la variable** , tapez un nom pour la nouvelle variable membre.

   - Dans la zone de liste **Type de variable** , sélectionnez **int** ou tapez *int*.

   Vous pouvez maintenant modifier votre code pour spécifier la case d’option qui doit apparaître sélectionnée. Par exemple, `m_radioBox1 = 0;` sélectionne la première case d’option du groupe.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Gérer les contrôles de boîte de dialogue](controls-in-dialog-boxes.md)<br/>
[Comment : ajouter, modifier ou supprimer des contrôles](adding-editing-or-deleting-controls.md)<br/>
[Comment : mettre en page des contrôles](arrangement-of-controls-on-dialog-boxes.md)<br/>