---
title: Modification des Tables d’accélérateurs (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 56e24efb-d06b-4ed9-8915-1f99f725e247
ms.openlocfilehash: dfa0c26132378bcbe8a7f5203351134d91746aa7
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232173"
---
# <a name="editing-accelerator-tables-c"></a>Modification des Tables d’accélérateurs (C++)

Dans un projet C++, vous pouvez modifier une table d’accélérateurs directement avec la modification sur place dans le **Accelerator** éditeur.

Les procédures ci-dessous font référence à l’utilisation des pages de propriétés standard, toutefois, la modification sur place et la méthode de page de propriété ont le même résultat. Modifications apportées à l’aide des pages de propriétés ou à l’aide de la modification sur place sont immédiatement répercutées dans la table d’accélérateurs.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

## <a name="to-edit-in-an-accelerator-table"></a>Pour modifier une table d'accélérateurs

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez une entrée dans la table et sélectionnez cette option pour activer la modification sur place.

1. Sélectionnez un élément dans la zone de liste déroulante fixe, ou tapez sur place pour apporter des modifications.

   - Pour [ID](id-property.md), sélectionnez dans la liste ou d’un type à modifier.

   - Pour [modificateur](../windows/accelerator-modifier-property.md), sélectionnez dans la liste.

   - Pour [clé](../windows/accelerator-key-property.md), sélectionnez dans la liste ou d’un type à modifier.

   - Pour [Type](../windows/accelerator-type-property.md), sélectionnez **ASCII** ou **VIRTKEY** dans la liste.

## <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Pour rechercher une entrée dans une table d'accélérateurs ouverte

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez un en-tête de colonne pour trier le contenu de la colonne par ordre alphabétique. Par exemple, sélectionnez **ID** pour afficher tous les ID dans votre table d’accélérateurs par ordre alphabétique.

Vous pouvez ensuite examiner la liste et rechercher l'entrée.

## <a name="to-add-an-entry-to-an-accelerator-table"></a>Pour ajouter une entrée à une table d'accélérateurs

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Avec le bouton droit dans la table d’accélérateurs et choisissez **nouvel accélérateur** dans le menu contextuel, ou sélectionnez l’entrée de la ligne vide en bas de la table.

1. Sélectionnez un [ID](id-property.md) dans la liste déroulante dans l’ID de zone ou tapez un nouvel ID dans le **ID** boîte.

1. Type de la [clé](../windows/accelerator-key-property.md) vous souhaitez utiliser comme accélérateur, ou avec le bouton droit et choisissez **enfoncée suivante** dans le menu contextuel pour définir une combinaison de touches (la **enfoncée suivante** commande est également disponible à partir de la **modifier** menu).

1. Modifier le [modificateur](../windows/accelerator-modifier-property.md) et [Type](../windows/accelerator-type-property.md), si nécessaire.

1. Appuyez sur **Entrée**.

   > [!NOTE]
   > Assurez-vous que tous les accélérateurs définis sont uniques. Vous pouvez avoir plusieurs combinaisons de touches affectées au même ID avec pas mal d’effet, par exemple, **Ctrl** + **P** et **F8** peuvent être assignées à ID_PRINT. Toutefois, avoir une combinaison de touches attribuée à plusieurs ID ne fonctionne pas correctement, par exemple, **Ctrl** + **Z** assignée à ID_SPELL_CHECK et ID_THESAURUS.

## <a name="to-delete-an-entry-from-an-accelerator-table"></a>Pour supprimer une entrée dans une table d'accélérateurs

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez l'entrée à supprimer. (Maintenez la **Ctrl** ou **MAJ** enfoncée tout en sélectionnant pour choisir plusieurs entrées.)

1. Avec le bouton droit et choisissez **supprimer** dans le menu contextuel (ou sélectionnez **supprimer** à partir de la **modifier** menu).

\- ou -

- Appuyez sur la **supprimer** clé.

## <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Pour déplacer ou copier une entrée de table d'accélérateurs vers un autre fichier de script de ressources

1. Ouvrez les tables d'accélérateurs dans les deux fichiers de script de ressources.

1. Sélectionnez l'entrée à déplacer.

1. À partir de la **modifier** menu, choisissez **copie** ou **couper**.

1. Sélectionnez une entrée dans le fichier de script de ressources cible.

1. À partir de la **modifier** menu, choisissez **coller**.

   > [!NOTE]
   > Vous pouvez également utiliser les touches de raccourci pour les opérations de copie et de collage.

## <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Pour modifier les propriétés de plusieurs touches accélérateur

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez les touches accélérateur que vous souhaitez modifier en maintenant enfoncée la **Ctrl** enfoncée quand vous sélectionnez chacun d’eux.

1. Accédez à la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) et tapez les valeurs que vous voulez que tous les accélérateurs sélectionnés doivent partager.

   > [!NOTE]
   > Chaque valeur de modificateur apparaît sous la forme d’une propriété booléenne dans la **propriétés** fenêtre. Si vous modifiez un [modificateur](../windows/accelerator-modifier-property.md) valeur dans le **propriétés** fenêtre, la table d’accélérateurs traite le nouveau modificateur comme un ajout aux modificateurs déjà présents. Pour cette raison, si vous définissez des valeurs de la modifier, vous devez définir tous pour vous assurer que chaque accélérateur partage les mêmes **modificateur** paramètres.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur d’accélérateurs](../windows/accelerator-editor.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)
