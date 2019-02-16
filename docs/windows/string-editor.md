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
ms.openlocfilehash: 8f33ef6d0198f083e7cf1b1e1dc2129be9b3fab4
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320560"
---
# <a name="string-editor-c"></a>Éditeur de chaînes (C++)

Une table de chaînes est une ressource Windows qui contient une liste d’ID, de valeurs et de légendes pour toutes les chaînes de votre application. Par exemple, les invites de la barre d’état figurent dans la table de chaînes.

Lors du développement d’une application, vous pouvez avoir plusieurs tables de chaînes, une pour chaque langue ou condition. Toutefois, un module exécutable n’a qu’une seule table de chaînes. Une application en cours d’exécution peut faire référence à plusieurs tables de chaînes si vous placez les tables dans différentes DLL.

Les tables de chaînes simplifient la localisation de votre application dans différentes langues. Si toutes les chaînes sont dans une table de chaînes, vous pouvez localiser l’application en traduisant les chaînes (et autres ressources) sans modifier le code source. Cette situation est plus intéressant que rechercher et remplacer des chaînes différentes dans les fichiers sources manuellement.

## <a name="how-to"></a>Procédure

Utilisez le **chaîne** éditeur pour les actions suivantes :

### <a name="to-find-a-string-resource-in-the-string-table"></a>Pour rechercher une ressource de chaîne dans la table de chaînes

Vous pouvez rechercher une ou plusieurs chaînes dans la table de chaînes et utiliser [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) avec la **rechercher dans les fichiers** commande (**modifier** menu) pour rechercher toutes les instances de chaînes qui correspondent à un modèle.

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sur le **modifier** menu, sélectionnez **rechercher et remplacer**, puis choisissez **trouver**.

1. Dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante ou tapez l’identificateur de texte ou de ressource de légende de la chaîne à rechercher.

1. Sélectionnez un de la **trouver** options.

1. Sélectionnez **Rechercher suivant**.

   > [!TIP]
   > Pour utiliser des expressions régulières lors de la recherche de fichiers, utilisez le **rechercher dans les fichiers** commande. Tapez une expression régulière pour correspondre à un modèle ou sélectionnez le bouton à droite de la **rechercher** à cocher pour afficher une liste des expressions régulières de recherche. Lorsque vous sélectionnez une expression à partir de cette liste, elle se substitue le texte de recherche dans les **rechercher** boîte. Si vous utilisez des expressions régulières, n’oubliez pas le **utiliser : Les Expressions régulières** case à cocher est activée.

### <a name="to-add-or-delete-a-string-resource"></a>Pour ajouter ou supprimer une ressource de chaîne

Vous pouvez rapidement insérer ou supprimer des entrées dans la table de chaîne à l’aide de la **chaîne** éditeur. Nouvelles chaînes sont placés à la fin de la table et sont fonction de l’identificateur de disponible suivant. Vous pouvez ensuite modifier le **ID**, **valeur**, ou **légende** propriétés dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) en fonction des besoins.

Le **chaîne** éditeur permet de s’assurer, vous n’utilisez pas un ID qui est déjà en cours d’utilisation. Si vous sélectionnez un ID déjà en cours d’utilisation, le **chaîne** éditeur sera vous avertir, puis attribuez un ID unique générique, par exemple `IDS_STRING58113`.

#### <a name="to-add-a-string-table-entry"></a>Pour ajouter une entrée de table de chaînes

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Avec le bouton droit dans la table de chaînes et choisissez **nouvelle chaîne** dans le menu contextuel.

1. Dans le **chaîne** éditeur, sélectionnez une **ID** à partir de la liste déroulante d’ID ou le type ID directement sur place.

1. Modifier le **valeur**, si nécessaire.

1. Tapez une entrée pour le **légende**.

   > [!NOTE]
   > Chaînes null ne sont pas autorisés dans les tables de chaînes de Windows. Si vous créez une entrée dans la table de chaînes est une chaîne null, vous recevrez un message vous invitant à « Veuillez entrer une chaîne pour cette entrée de table ».

#### <a name="to-delete-a-string-table-entry"></a>Pour supprimer une entrée de table de chaînes

Sélectionnez l'entrée à supprimer. Effectuez ensuite l'une des opérations suivantes :

- Sur le **modifier** menu, sélectionnez **supprimer**.

- Avec le bouton droit de la chaîne que vous souhaitez supprimer, puis sélectionnez **supprimer** dans le menu contextuel.

- Appuyez sur la **supprimer** clé.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Déplacer une chaîne à partir du fichier de script d’une ressource à un autre

1. Ouvrez les tables de chaînes dans les deux fichiers .rc. (Pour plus d’informations, consultez [affichage des ressources dans un fichier de Script de ressources en dehors d’un projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)

1. Avec le bouton droit de la chaîne que vous souhaitez déplacer et choisissez **couper** dans le menu contextuel.

1. Placez le curseur dans la cible **éditeur de chaînes** fenêtre.

1. Dans le fichier .rc vers lequel vous souhaitez déplacer la chaîne, avec le bouton droit et choisissez **coller** dans le menu contextuel.

   > [!NOTE]
   > Si le **ID** ou **valeur** de conflits avec une chaîne déplacée **ID** ou **valeur** dans le fichier de destination, soit le **ID** ou **valeur** des modifications de chaîne déplacée. S’il existe une chaîne avec le même **ID**, le **ID** des modifications de chaîne déplacée. S’il existe une chaîne avec le même **valeur**, le **valeur** des modifications de chaîne déplacée.

### <a name="to-change-the-properties-of-a-string-resource"></a>Pour modifier les propriétés d’une ressource de chaîne

Vous pouvez utiliser la modification sur place pour modifier le code, valeur et les propriétés de légende.

#### <a name="to-change-a-string-or-its-identifier"></a>Pour modifier une chaîne ou son identificateur

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez la chaîne que vous souhaitez modifier, puis double-cliquez sur le **ID**, **valeur**, ou **légende** colonne. Vous pouvez désormais :

   - Sélectionnez un **ID** à partir de la **ID de liste déroulante** liste ou tapez une `ID` directement en place.

   - Tapez un nombre différent dans le **valeur** colonne.

   - Taper des modifications dans le **légende** colonne.

        > [!NOTE]
        >  Vous pouvez également modifier les propriétés d’une chaîne dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Pour modifier la propriété caption de plusieurs ressources de type chaîne

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez les chaînes que vous souhaitez modifier en maintenant enfoncée la **Ctrl** enfoncée quand vous sélectionnez chacun d’eux.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez une nouvelle valeur pour la propriété que vous souhaitez modifier.

1. Appuyez sur **Entrée**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Pour ajouter des caractères spéciaux ou de mise en forme à une ressource de chaîne

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez la chaîne que vous souhaitez modifier.

1. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ajouter du texte dans des séquences d’échappement standard figurant ci-dessous le **légende** zone, puis appuyez sur **entrée**.

   |Pour résoudre ce|Ce type|
   |-----------------|---------------|
   | Nouvelle ligne | \\n |
   | Retour chariot | \\r |
   | Onglet | \\t |
   | Barre oblique inverse (\\) | \\\\ |
   | Caractère ASCII | \\ddd (notation octale) |
   | alerte (clochette) | \\a |

> [!NOTE]
> Le **chaîne** éditeur ne prend pas en charge l’ensemble complet d’échappement des caractères d’ASCII. Vous ne pouvez utiliser que ceux répertoriés ci-dessus.

> [!NOTE]
> Windows n’autorise pas la création de tables de chaînes vides. Si vous créez une table de chaînes sans entrée, elle est supprimée automatiquement lorsque vous enregistrez le fichier de ressources.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Chaînes](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[À propos des chaînes](/windows/desktop/menurc/about-strings)<br/>
[Personnalisation des dispositions de fenêtres](/visualstudio/ide/customizing-window-layouts-in-visual-studio)