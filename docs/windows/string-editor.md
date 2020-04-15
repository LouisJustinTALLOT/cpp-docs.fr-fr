---
title: Éditeur de cordes (CMD)
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
ms.openlocfilehash: b0fb077752cf1912e07175c68cdc8acfe758b0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370241"
---
# <a name="string-editor-c"></a>Éditeur de cordes (CMD)

Une table de chaînes est une ressource Windows qui contient une liste d’ID, de valeurs et de légendes pour toutes les chaînes de votre application. Par exemple, les invites de la barre d’état figurent dans la table de chaînes.

Lors du développement d’une application, vous pouvez avoir plusieurs tables de chaînes, une pour chaque langue ou condition. Toutefois, un module exécutable n’a qu’une seule table de chaînes. Une application en cours d’exécution peut faire référence à plusieurs tables de chaînes si vous placez les tables dans différentes DLL.

Les tables de chaînes simplifient la localisation de votre application dans différentes langues. Si toutes les chaînes sont dans une table de chaînes, vous pouvez localiser l’application en traduisant les chaînes (et autres ressources) sans modifier le code source. Cette situation est plus souhaitable que de trouver et de remplacer manuellement diverses chaînes dans les fichiers sources.

> [!NOTE]
> Windows ne permet pas la création de tables à cordes vides. Si vous créez une table de chaînes sans entrée, elle est supprimée automatiquement lorsque vous enregistrez le fichier de ressources.

## <a name="how-to"></a>Procédure

**L’éditeur à cordes** vous permet :

### <a name="to-find-a-string-resource-in-the-string-table"></a>Pour trouver une ressource de chaîne dans la table à cordes

1. Ouvrez la table à cordes en cliquant à deux clics sur son icône dans [Resource View](how-to-create-a-resource-script-file.md#create-resources).

1. Aller au menu **Modifier** > **Trouver et remplacer** et choisir **Trouver**.

1. Dans la case **Trouver quoi,** sélectionnez une chaîne de recherche précédente de la liste d’abandon, ou tapez le texte de légende ou l’identifiant de ressources de la chaîne que vous souhaitez trouver.

1. Sélectionnez l’une des options **Trouver** et sélectionnez **Trouver ensuite**.

> [!TIP]
> Pour utiliser [des expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) lors de la recherche de fichiers, utilisez la commande Trouver dans les **fichiers** dans le menu **Modifier.**
>
> Tapez une expression régulière pour correspondre à un motif ou sélectionnez le bouton à droite de la case **Trouver quelle** pour afficher une liste d’expressions de recherche régulières. Lorsque vous sélectionnez une expression de cette liste, elle est substituée sous forme de texte de recherche dans la case **Trouver quelle.**
>
> Si vous utilisez des expressions régulières, assurez-vous que la case à cocher **Use: Regular Expressions** est sélectionnée.

### <a name="to-add-or-delete-a-string-resource"></a>Pour ajouter ou supprimer une ressource de chaîne

Vous pouvez rapidement insérer ou supprimer des entrées dans la table de chaîne à l’aide de **l’éditeur de cordes**. De nouvelles chaînes sont placées à la fin de la table et reçoivent le prochain identifiant disponible. Vous pouvez modifier les propriétés **ID,** **Value**, ou **Caption** dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) au besoin.

**L’éditeur de cordes** s’assure de ne pas utiliser une pièce d’identité qui est déjà utilisée. Si vous sélectionnez un ID déjà utilisé, **l’éditeur à cordes** vous `IDS_STRING58113`avisera et attribuera ensuite un IDENTIFIANT unique générique, par exemple .

#### <a name="to-add-a-string-table-entry"></a>Pour ajouter une entrée de table à cordes

1. Ouvrez la table à cordes en cliquant à deux clics sur son icône dans [Resource View](how-to-create-a-resource-script-file.md#create-resources).

1. Cliquez à droite dans la table de chaîne et choisissez **New String**.

1. Dans **l’éditeur de cordes**, sélectionnez une **pièce d’identité** de la liste **d’abandon d’identité** ou tapez une *pièce d’identité* directement en place.

1. Modifier la **valeur**, si nécessaire.

1. Tapez une entrée pour la **Légende**.

   > [!NOTE]
   > Les cordes nulles ne sont pas autorisées dans les tables à cordes Windows. Si vous créez une entrée dans la table de chaîne qui est une corde nulle, vous recevrez un message vous demandant **de s’il vous plaît entrer une chaîne pour cette entrée de table**.

#### <a name="to-delete-a-string-table-entry"></a>Supprimer une entrée de table à cordes

Sélectionnez l’entrée que vous souhaitez supprimer et faites l’une des suivantes :

- Aller au menu **Edit** > **Supprimer**.

- Cliquez à droite sur la chaîne pour supprimer et choisir **Supprimer**.

- Appuyez sur la clé **Supprimer.**

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Déplacer une chaîne d’un fichier de script de ressource à un autre

1. [Ouvrez les tables de cordes dans les deux fichiers .rc](../windows/how-to-create-a-resource-script-file.md).

1. Cliquez à droite sur la chaîne pour bouger et choisir **Cut**.

1. Placez le curseur dans la fenêtre **cible string Editor.**

1. Dans le fichier *.rc* auquel vous souhaitez déplacer la chaîne, clic droit et choisir **Pâte**.

> [!NOTE]
> Si **l’ID** ou la **valeur** de la chaîne déplacée entre en conflit avec une **pièce d’identité** ou une **valeur** existante dans le fichier de destination, soit cette **pièce d’identité** ou la **valeur** de la chaîne déplacée change.

### <a name="to-change-the-properties-of-a-string-resource"></a>Pour changer les propriétés d’une ressource à cordes

Vous pouvez utiliser l’édition sur place pour modifier les propriétés **ID,** **Value**et **Caption.**

> [!NOTE]
> Vous pouvez également modifier les propriétés d’une chaîne dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Pour changer une chaîne ou son identifiant

1. Ouvrez la table à cordes en cliquant à deux clics sur son icône dans [Resource View](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez la chaîne que vous souhaitez modifier et doublez **l’ID,** **La valeur,** ou la colonne **caption,** alors vous pouvez :

   - Sélectionnez une **pièce d’identité** de la liste **d’accueil d’identification** ou tapez un *ID* directement en place.

   - Tapez un nombre différent dans la colonne **De** valeur.

   - Type de modifications dans la colonne **Caption.**

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Pour changer la propriété de légende de plusieurs ressources de chaîne

1. Ouvrez la table à cordes en cliquant à deux clics sur son icône dans [Resource View](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez les chaînes que vous souhaitez modifier en maintenant la clé **Ctrl** lorsque vous sélectionnez chacune d’elles.

1. Dans la [fenêtre des propriétés](/visualstudio/ide/reference/properties-window), tapez une nouvelle valeur pour la propriété que vous souhaitez changer.

1. Appuyez sur **Entrée**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Pour ajouter le formatage ou des caractères spéciaux à une ressource de chaîne

1. Ouvrez la table à cordes en cliquant à deux clics sur son icône dans [Resource View](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez la chaîne que vous souhaitez modifier.

1. Dans la [fenêtre propriétés](/visualstudio/ide/reference/properties-window), ajouter l’une des séquences d’évasion standard énumérées ci-dessous au texte dans la boîte **de légende** et appuyez **sur Enter**.

   |Pour obtenir ce ...|Tapez ceci...|
   |-----------------|---------------|
   | Nouvelle ligne | \\n |
   | Retour chariot | \\R |
   | Onglet | \\t |
   | Barre oblique inverse (\\) | \\\\ |
   | Caractère ASCII | \\ddd (notation octale) |
   | Alerte (cloche) | \\a |

   > [!NOTE]
   > **L’éditeur de cordes** ne prend pas en charge l’ensemble complet des personnages ASCI échappés. Vous ne pouvez utiliser que ceux énumérés ci-dessus.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Chaînes de rédacteurs](../windows/resource-editors.md)
en chef[de ressources](/windows/win32/menurc/strings)<br/>
[À propos des chaînes](/windows/win32/menurc/about-strings)<br/>
[Personnalisation des dispositions de fenêtres](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
