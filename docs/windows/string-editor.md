---
title: Éditeur de chaînesC++()
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
ms.openlocfilehash: 996e5f132e5cfa33c39c4cc3ddbeb692f41925bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514717"
---
# <a name="string-editor-c"></a>Éditeur de chaînesC++()

Une table de chaînes est une ressource Windows qui contient une liste d’ID, de valeurs et de légendes pour toutes les chaînes de votre application. Par exemple, les invites de la barre d’état figurent dans la table de chaînes.

Lors du développement d’une application, vous pouvez avoir plusieurs tables de chaînes, une pour chaque langue ou condition. Toutefois, un module exécutable n’a qu’une seule table de chaînes. Une application en cours d’exécution peut faire référence à plusieurs tables de chaînes si vous placez les tables dans différentes DLL.

Les tables de chaînes simplifient la localisation de votre application dans différentes langues. Si toutes les chaînes sont dans une table de chaînes, vous pouvez localiser l’application en traduisant les chaînes (et autres ressources) sans modifier le code source. Cette situation est plus souhaitable que la recherche et le remplacement manuels de différentes chaînes dans les fichiers sources.

> [!NOTE]
> Windows n’autorise pas la création de tables de chaînes vides. Si vous créez une table de chaînes sans entrée, elle est supprimée automatiquement lorsque vous enregistrez le fichier de ressources.

## <a name="how-to"></a>Comment

L' **éditeur de chaînes** vous permet d’activer les éléments suivants :

### <a name="to-find-a-string-resource-in-the-string-table"></a>Pour rechercher une ressource de type chaîne dans la table de chaînes

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Accédez au menu **modifier** > **Rechercher et remplacer** , puis cliquez sur **Rechercher**.

1. Dans la zone **Rechercher** , sélectionnez une chaîne de recherche précédente dans la liste déroulante ou tapez le texte de légende ou l’identificateur de ressource de la chaîne que vous souhaitez rechercher.

1. Sélectionnez l’une des options de **recherche** , puis sélectionnez **suivant**.

> [!TIP]
> Pour utiliser des [expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) lors de la recherche de fichiers, utilisez la commande **Rechercher dans les fichiers** du menu **Edition** .
>
> Tapez une expression régulière correspondant à un modèle ou sélectionnez le bouton à droite de la zone **Rechercher** pour afficher une liste d’expressions de recherche standard. Lorsque vous sélectionnez une expression dans cette liste, elle est remplacée par le texte recherché dans la zone **Rechercher** .
>
> Si vous utilisez des expressions régulières, veillez **à utiliser : La case** à cocher expressions régulières est activée.

### <a name="to-add-or-delete-a-string-resource"></a>Pour ajouter ou supprimer une ressource de type chaîne

Vous pouvez insérer ou supprimer rapidement des entrées dans la table de chaînes à l’aide de l' **éditeur de chaînes**. Les nouvelles chaînes sont placées à la fin de la table et reçoivent le prochain identificateur disponible. Vous pouvez modifier les propriétés **ID**, **value**ou **Caption** dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) en fonction des besoins.

L' **éditeur de chaînes** vérifie que vous n’utilisez pas un ID qui est déjà en cours d’utilisation. Si vous sélectionnez un ID qui est déjà utilisé, l' **éditeur de chaînes** vous en informe, puis affecte un ID unique générique, `IDS_STRING58113`par exemple.

#### <a name="to-add-a-string-table-entry"></a>Pour ajouter une entrée de table de chaînes

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Cliquez avec le bouton droit dans la table de chaînes et choisissez **nouvelle chaîne**.

1. Dans l' **éditeur de chaînes**, sélectionnez **un ID** dans la liste déroulante **ID** ou tapez un *ID* directement sur place.

1. Modifiez la **valeur**, si nécessaire.

1. Tapez une entrée pour la **légende**.

   > [!NOTE]
   > Les chaînes NULL ne sont pas autorisées dans les tables de chaînes Windows. Si vous créez une entrée dans la table de chaînes qui est une chaîne NULL, vous recevrez un message vous invitant à **entrer une chaîne pour cette entrée de table**.

#### <a name="to-delete-a-string-table-entry"></a>Pour supprimer une entrée de table de chaînes

Sélectionnez l’entrée que vous souhaitez supprimer et effectuez l’une des opérations suivantes :

- Accédez au menu **modifier** > **supprimer**.

- Cliquez avec le bouton droit sur la chaîne à supprimer, puis sélectionnez **supprimer**.

- Appuyez sur la touche **Suppr** .

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Pour déplacer une chaîne d’un fichier de script de ressources vers un autre

1. [Ouvrez les tables de chaînes dans les deux fichiers. RC](../windows/how-to-create-a-resource-script-file.md).

1. Cliquez avec le bouton droit sur la chaîne à déplacer, puis choisissez **couper**.

1. Placez le curseur dans la fenêtre de l' **éditeur de chaîne** cible.

1. Dans le fichier *. RC* vers lequel vous souhaitez déplacer la chaîne, cliquez avec le bouton droit et choisissez **coller**.

> [!NOTE]
> Si l' **ID** ou la **valeur** de la chaîne déplacée est en conflit avec un **ID** ou une **valeur** existant dans le fichier de destination, soit cet **ID** , soit la **valeur** de la chaîne déplacée change.

### <a name="to-change-the-properties-of-a-string-resource"></a>Pour modifier les propriétés d’une ressource de type chaîne

Vous pouvez utiliser la modification sur place pour modifier les propriétés **ID**, **value**et **Caption** .

> [!NOTE]
>  Vous pouvez également modifier les propriétés d’une chaîne dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Pour modifier une chaîne ou son identificateur

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez la chaîne que vous souhaitez modifier, puis double-cliquez sur la colonne **ID**, **valeur**ou **légende** . vous pouvez alors :

   - Sélectionnez un **ID** dans la liste déroulante **ID** , ou tapez un *ID* directement sur place.

   - Tapez un autre nombre dans la colonne **valeur** .

   - Tapez des modifications dans la colonne **légende** .

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Pour modifier la propriété de légende de plusieurs ressources de type chaîne

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez les chaînes que vous souhaitez modifier en maintenant la touche **CTRL** enfoncée tout en sélectionnant chacune d’elles.

1. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez une nouvelle valeur pour la propriété que vous souhaitez modifier.

1. Appuyez sur **Entrée**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Pour ajouter une mise en forme ou des caractères spéciaux à une ressource de type chaîne

1. Ouvrez la table de chaînes en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez la chaîne que vous souhaitez modifier.

1. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), ajoutez l’une des séquences d’échappement standard listées ci-dessous au texte de la zone **légende** et appuyez sur **entrée**.

   |Pour ce faire...|Tapez...|
   |-----------------|---------------|
   | Nouvelle ligne | \\n |
   | Retour chariot | \\r |
   | Onglet | \\t |
   | Barre oblique inverse (\\) | \\\\ |
   | Caractère ASCII | \\DDD (notation octale) |
   | Alerte (cloche) | \\a |

   > [!NOTE]
   > L' **éditeur de chaînes** ne prend pas en charge l’ensemble complet des caractères ASCI échappés. Vous ne pouvez utiliser que ceux listés ci-dessus.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Chaînes](/windows/win32/menurc/strings) des [éditeurs de ressources](../windows/resource-editors.md)
<br/>
[À propos des chaînes](/windows/win32/menurc/about-strings)<br/>
[Personnalisation des dispositions de fenêtres](/visualstudio/ide/customizing-window-layouts-in-visual-studio)