---
title: Définition des valeurs et contrôler l’accès
ms.date: 11/04/2016
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
ms.openlocfilehash: 3a885ad57ba05304d51cb45d0b498d81ad37a148
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264853"
---
# <a name="defining-control-access-and-values"></a>Définition des valeurs et contrôler l’accès

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="change-the-tab-order-of-controls"></a>Modifier l’ordre de tabulation des contrôles

L’ordre de tabulation est l’ordre dans lequel le **onglet** touche déplace le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue. Généralement, l’ordre de tabulation se déroule de gauche à droite et de haut en bas dans une boîte de dialogue. Chaque contrôle possède une **Tabstop** propriété qui détermine si un contrôle reçoit le focus d’entrée.

### <a name="to-set-input-focus-for-a-control"></a>Pour définir le focus d’entrée pour un contrôle

Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), sélectionnez **True** ou **False** dans le **Tabstop** propriété.

Même les contrôles qui n’ont pas la **Tabstop** propriété définie sur **True** doivent faire partie de l’ordre de tabulation. Ordre de tabulation est important, par exemple, lorsque vous [définir des touches d’accès rapide (mnémoniques)](../windows/defining-mnemonics-access-keys.md) pour les contrôles qui n’ont pas des légendes. Texte statique qui contient une clé d’accès pour un contrôle lié doit précéder immédiatement le contrôle concerné dans l’ordre de tabulation.

> [!NOTE]
> Si votre boîte de dialogue contient des contrôles qui se chevauchent, la modification de l’ordre de tabulation peut changer la façon des que contrôles sont affichés. Contrôles fournis plus loin dans l’ordre de tabulation sont toujours affichés au-dessus des contrôles superposés qui les précèdent dans l’ordre de tabulation.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Pour afficher l’ordre de tabulation actuel pour tous les contrôles dans une boîte de dialogue

Sur le **Format** menu, sélectionnez **l’ordre de tabulation**.

\- ou -

- Appuyez sur **Ctrl** + **D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Pour modifier l’ordre de tabulation pour tous les contrôles dans une boîte de dialogue

1. Sur le **Format** menu, sélectionnez **l’ordre de tabulation**.

   Un nombre dans le coin supérieur gauche de chaque contrôle affiche sa place dans l’ordre de tabulation en cours.

1. Définir l’ordre de tabulation en cliquant sur chaque contrôle dans l’ordre que vous souhaitez que le **onglet** clé à suivre.

1. Appuyez sur **entrée** pour quitter **l’ordre de tabulation** mode.

   > [!TIP]
   > Une fois que vous entrez **l’ordre de tabulation** mode, vous pouvez appuyer sur **ÉCHAP** ou **entrée** pour désactiver la possibilité de modifier l’ordre de tabulation.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Pour modifier l’ordre de tabulation pour deux ou plusieurs contrôles

1. À partir de la **Format** menu, choisissez **l’ordre de tabulation**.

1. Spécifier où commence la modification dans l’ordre. Maintenez tout d’abord le **Ctrl** de clé et sélectionnez le contrôle, puis sélectionnez celui dans lequel vous souhaitez modifier l’ordre.

   Par exemple, si vous souhaitez modifier l’ordre des contrôles `7` via `9`, maintenez la touche **Ctrl**, puis sélectionnez le contrôle `6` première.

   > [!NOTE]
   > Pour affecter à un contrôle spécifique numéro `1` (tout d’abord dans l’ordre de tabulation), double-cliquez sur le contrôle.

1. Mise en production la **Ctrl** de clé, puis sélectionnez les contrôles dans l’ordre que vous souhaitez que le **onglet** à partir de ce point.

1. Appuyez sur **entrée** pour quitter **l’ordre de tabulation** mode.

## <a name="define-mnemonics-access-keys"></a>Définition des mnémoniques (touches d’accès rapide)

En règle générale, les utilisateurs du clavier déplacent le focus d’entrée d’un contrôle à l’autre dans une boîte de dialogue avec le **onglet** et **flèche** clés. Toutefois, vous pouvez définir une clé d’accès (un nom mnémonique ou facile à mémoriser) qui permet aux utilisateurs de choisir un contrôle en appuyant sur une clé unique.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Pour définir une clé d’accès pour un contrôle avec une légende visible (boutons de commande, cases à cocher et des boutons radio)

1. Sélectionnez le contrôle dans la boîte de dialogue.

2. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), dans le **légende** propriété, tapez un nouveau nom pour le contrôle en tapant une esperluette (`&`) devant la lettre que vous souhaitez comme touche d’accès pour ce contrôle. Par exemple, `&Radio1`.

3. Appuyez sur **Entrée**.

   Un trait de soulignement apparaît dans la légende pour indiquer la clé d’accès, par exemple, **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Pour définir une clé d’accès pour un contrôle sans légende visible

1. Créez une légende pour le contrôle à l’aide un **texte statique** dans contrôler le [boîte à outils](/visualstudio/ide/reference/toolbox).

2. Dans la légende de texte statique, tapez une esperluette (`&`) devant la lettre que vous souhaitez comme touche d’accès.

3. Assurez-vous que le contrôle de texte statique précède immédiatement le contrôle qu’il identifie dans l’ordre de tabulation.

Toutes les clés d’accès au sein d’une boîte de dialogue doivent être uniques.

### <a name="to-check-for-duplicate-access-keys"></a>Pour vérifier les clés d’accès en double

1. Sur le **Format** menu, cliquez sur **vérifier les mnémoniques**.

## <a name="add-values-to-a-combo-box-control"></a>Ajouter des valeurs à un contrôle combo box

Vous pouvez ajouter des valeurs à un contrôle combo box tant que vous avez le **boîte de dialogue** éditeur ouvert.

> [!TIP]
> Il est judicieux d’ajouter toutes les valeurs à la zone de liste déroulante *avant* dimensionner la zone dans le **boîte de dialogue** éditeur ou texte qui doit apparaître dans le contrôle de liste déroulante peut être tronqué.

### <a name="to-enter-values-into-a-combo-box-control"></a>Pour entrer des valeurs dans un contrôle combo box

1. Sélectionnez le contrôle de zone de liste modifiable en cliquant dessus.

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

Après avoir entré les valeurs dans le **données** propriété, sélectionnez le **Test** bouton sur le [barre d’outils Éditeur de boîte de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

   Faites défiler vers le bas la liste de valeur entière. Les valeurs s’affichent exactement comme ils sont tapés dans le **données** propriété dans le **propriétés** fenêtre. Il n’existe aucune orthographe ou la vérification de la mise en majuscules.

   Appuyez sur **ÉCHAP** pour revenir à la **boîte de dialogue** éditeur.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)