---
title: Éditeur de chaînes (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: 6c855986d98f265f876f2acdd085eea46e057c93
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328894"
---
# <a name="string-editor-c"></a>Éditeur de chaînes (C++)

Une table de chaînes est une ressource Windows qui contient une liste d’ID, de valeurs et de légendes pour toutes les chaînes de votre application. Par exemple, les invites de la barre d’état figurent dans la table de chaînes.

Lors du développement d’une application, vous pouvez avoir plusieurs tables de chaînes, une pour chaque langue ou condition. Toutefois, un module exécutable n’a qu’une seule table de chaînes. Une application en cours d’exécution peut faire référence à plusieurs tables de chaînes si vous placez les tables dans différentes DLL.

Les tables de chaînes simplifient la localisation de votre application dans différentes langues. Si toutes les chaînes sont dans une table de chaînes, vous pouvez localiser l’application en traduisant les chaînes (et autres ressources) sans modifier le code source. Cette situation est plus intéressant que rechercher et remplacer des chaînes différentes dans les fichiers sources manuellement.

> [!NOTE]
> Windows n’autorise pas la création de tables de la chaîne vide. Si vous créez une table de chaînes sans entrée, elle est supprimée automatiquement lorsque vous enregistrez le fichier de ressources.

## <a name="how-to"></a>Comment

Le **éditeur de chaînes** vous permet de :

### <a name="to-find-a-string-resource-in-the-string-table"></a>Pour rechercher une ressource de chaîne dans la table de chaînes

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Accédez au menu **modifier** > **rechercher et remplacer** et choisissez **trouver**.

1. Dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante, ou tapez l’identificateur de texte ou de ressource de légende de la chaîne à rechercher.

1. Sélectionnez un de la **trouver** options et sélectionnez **suivant**.

> [!TIP]
> Pour utiliser [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) lors de la recherche de fichiers, utilisez le **rechercher dans les fichiers** commande dans le **modifier** menu.
>
> Tapez une expression régulière pour correspondre à un modèle ou sélectionnez le bouton à droite de la **rechercher** à cocher pour afficher une liste des expressions régulières de recherche. Lorsque vous sélectionnez une expression à partir de cette liste, elle se substitue le texte de recherche dans les **rechercher** boîte.
>
> Si vous utilisez des expressions régulières, n’oubliez pas le **utiliser : Les Expressions régulières** case à cocher est activée.

### <a name="to-add-or-delete-a-string-resource"></a>Pour ajouter ou supprimer une ressource de chaîne

Vous pouvez rapidement insérer ou supprimer des entrées dans la table de chaîne à l’aide de la **éditeur de chaînes**. Nouvelles chaînes sont placés à la fin de la table et sont fonction de l’identificateur de disponible suivant. Vous pouvez modifier le **ID**, **valeur**, ou **légende** propriétés dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) en fonction des besoins.

Le **éditeur de chaînes** permet de s’assurer que vous n’utilisez pas un ID qui est déjà en cours d’utilisation. Si vous sélectionnez un ID déjà en cours d’utilisation, le **éditeur de chaînes** sera vous avertir, puis attribuez un ID unique générique, par exemple `IDS_STRING58113`.

#### <a name="to-add-a-string-table-entry"></a>Pour ajouter une entrée de table de chaînes

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Avec le bouton droit dans la table de chaînes et choisissez **nouvelle chaîne**.

1. Dans le **éditeur de chaînes**, sélectionnez un **ID** à partir de la **ID** type ou liste déroulante une *ID* directement en place.

1. Modifier le **valeur**, si nécessaire.

1. Tapez une entrée pour le **légende**.

   > [!NOTE]
   > Chaînes null ne sont pas autorisés dans les tables de chaînes de Windows. Si vous créez une entrée dans la table de chaînes est une chaîne null, vous recevrez un message vous demandant de **Veuillez entrer une chaîne pour cette entrée de table**.

#### <a name="to-delete-a-string-table-entry"></a>Pour supprimer une entrée de table de chaînes

Sélectionnez l’entrée que vous souhaitez supprimer, puis effectuez l’une des opérations suivantes :

- Accédez au menu **modifier** > **supprimer**.

- Avec le bouton droit de la chaîne à supprimer, puis choisissez **supprimer**.

- Appuyez sur la **supprimer** clé.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Déplacer une chaîne à partir du fichier de script d’une ressource à un autre

1. [Ouvrez les tables de chaînes dans les deux fichiers .rc](../windows/how-to-create-a-resource-script-file.md).

1. Avec le bouton droit de la chaîne pour déplacer et choisissez **couper**.

1. Placez le curseur dans la cible **éditeur de chaînes** fenêtre.

1. Dans le *.rc* fichier auquel vous souhaitez déplacer la chaîne, avec le bouton droit et choisissez **coller**.

> [!NOTE]
> Si le **ID** ou **valeur** de conflits avec une chaîne déplacée **ID** ou **valeur** dans le fichier de destination, soit ce **ID** ou **valeur** des modifications de chaîne déplacée.

### <a name="to-change-the-properties-of-a-string-resource"></a>Pour modifier les propriétés d’une ressource de chaîne

Vous pouvez utiliser la modification sur place pour modifier le **ID**, **valeur**, et **légende** propriétés.

> [!NOTE]
>  Vous pouvez également modifier les propriétés d’une chaîne dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Pour modifier une chaîne ou son identificateur

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez la chaîne que vous souhaitez modifier, puis double-cliquez sur le **ID**, **valeur**, ou **légende** colonne, vous pouvez :

   - Sélectionnez un **ID** à partir de la **ID** liste de liste déroulante ou tapez une *ID* directement en place.

   - Tapez un nombre différent dans le **valeur** colonne.

   - Taper des modifications dans le **légende** colonne.

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Pour modifier la propriété caption de plusieurs ressources de type chaîne

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez les chaînes que vous souhaitez modifier en maintenant enfoncée la **Ctrl** enfoncée quand vous sélectionnez chacun d’eux.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez une nouvelle valeur pour la propriété que vous souhaitez modifier.

1. Appuyez sur **Entrée**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Pour ajouter des caractères spéciaux ou de mise en forme à une ressource de chaîne

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez la chaîne que vous souhaitez modifier.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ajouter du texte dans des séquences d’échappement standard figurant ci-dessous le **légende** zone et appuyez sur **entrée**.

   |Pour obtenir ceci...|Tapez ceci...|
   |-----------------|---------------|
   | Nouvelle ligne | \\n |
   | Retour chariot | \\r |
   | Onglet | \\t |
   | Barre oblique inverse (\\) | \\\\ |
   | Caractère ASCII | \\ddd (notation octale) |
   | alerte (clochette) | \\a |

   > [!NOTE]
   > Le **éditeur de chaînes** ne prend pas en charge l’ensemble complet d’échappement des caractères d’ASCII. Vous ne pouvez utiliser que ceux répertoriés ci-dessus.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)
<!--
[Strings](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[About Strings](/windows/desktop/menurc/about-strings)<br/>
[Customizing window layouts](/visualstudio/ide/customizing-window-layouts-in-visual-studio)-->