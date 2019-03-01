---
title: Éditeur d’accélérateurs (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
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
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: 21f588f6103195d9fe977d0b019b911b33f43105
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210833"
---
# <a name="accelerator-editor-c"></a>Éditeur d’accélérateurs (C++)

Une table d’accélérateurs est une ressource C++ Windows qui contient une liste des touches accélérateur (également connu sous les touches de raccourci) et les identificateurs de commande qui leur sont associés. Un programme peut avoir plusieurs tables d’accélérateurs.

Normalement, les accélérateurs sont utilisés comme raccourcis clavier pour des commandes de programme qui sont également disponibles dans un menu ou une barre d’outils. Toutefois, vous pouvez utiliser la table d’accélérateurs pour définir des combinaisons de touches pour des commandes qui ne sont associées à aucun objet d’interface utilisateur.

Vous pouvez utiliser [Affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) pour raccorder des commandes de touches accélérateur à du code.

Pour une liste des touches accélérateur prédéfinies, consultez [touches accélérateur](../windows/predefined-accelerator-keys.md).

> [!TIP]
> Lorsque vous utilisez le **Éditeur d’accélérateurs**, avec le bouton droit pour afficher un menu contextuel de commandes fréquentes. Les commandes disponibles varient selon la cible du pointeur.

> [!NOTE]
> Windows ne vous permet de créer des tables d’accélérateurs vides. Si vous créez une table d’accélérateurs sans entrée, elle est supprimée automatiquement lorsque vous l’enregistrez.

## <a name="accelerator-properties"></a>Propriétés d’un accélérateur

Vous pouvez définir les propriétés d’un accélérateur dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) à tout moment. Vous pouvez également utiliser le **Éditeur d’accélérateurs** pour modifier les propriétés d’un accélérateur dans la table d’accélérateurs. Modifications apportées à l’aide de la **propriétés** fenêtre ou le **Éditeur d’accélérateurs** ont le même résultat, elles sont immédiatement répercutées dans la table d’accélérateurs.

### <a name="id-property"></a>ID, propriété

Le **ID** propriété fait référence à chaque entrée de table d’accélérateurs dans le code de programme. Cette entrée est la valeur de la commande que le programme reçoit lorsqu’un utilisateur appuie sur la touche accélérateur ou une combinaison de touches. Pour apporter un accélérateur identique à un élément de menu, vérifiez leur **ID** les mêmes, pourvu que la **ID** de l’accélérateur de table est identique à la **ID** pour la ressource de menu.

Il existe trois propriétés pour chaque accélérateur **ID**: **Modificateur**, **clé**, et **Type**

#### <a name="modifier-property"></a>Modifier, propriété

Le **modificateur** propriété définit les combinaisons de touches pour l’accélérateur de contrôle.

> [!NOTE]
> Dans le **propriétés** fenêtre, le **modificateur** propriété s’affiche en tant que distinct trois **booléenne** propriétés, qui peuvent être contrôlées indépendamment : **ALT**, **Ctrl**, et **MAJ**.

Les éléments suivants sont des entrées valides pour le **modificateur** propriété dans la table d’accélérateurs :

   |Value|Description|
   |-----------|-----------------|
   |**Aucun**|Utilisateur appuie sur uniquement le **clé** valeur. Cette valeur est utilisée plus efficacement avec les valeurs ASCII/ANSI 001 à 026, qui est interprétée comme ^ A à ^ Z (**Ctrl + A** via **Ctrl + Z**).|
   |**Alt**|L’utilisateur doit appuyer sur **Alt** avant la **clé** valeur.|
   |**Ctrl**|L’utilisateur doit appuyer sur **Ctrl** avant la **clé** valeur. Non valide avec le Type ASCII.|
   |**Maj**|L’utilisateur doit appuyer sur **MAJ** avant la **clé** valeur.|
   |**Ctrl+Alt**|L’utilisateur doit appuyer sur **Ctrl** et **Alt** avant la **clé** valeur. Non valide avec le Type ASCII.|
   |**CTRL + MAJ**|L’utilisateur doit appuyer sur **Ctrl** et **MAJ** avant la **clé** valeur. Non valide avec le Type ASCII.|
   |**ALT + MAJ**|L’utilisateur doit appuyer sur **Alt** et **MAJ** avant la **clé** valeur. Non valide avec le Type ASCII.|
   |**Ctrl+Alt+Shift**|L’utilisateur doit appuyer sur **Ctrl**, **Alt**, et **MAJ** avant la **clé** valeur. Non valide avec le Type ASCII.|

#### <a name="key-property"></a>Propriété de clé

Le **clé** propriété définit la clé réelle à utiliser comme accélérateur.

Les éléments suivants sont des entrées valides pour le **clé** propriété dans la table d’accélérateurs :

   |Value|Description|
   |-----------|-----------------|
   |Entier compris entre 0 et 255 au format décimal.|La valeur détermine si la valeur est traitée comme ASCII ou ANSI comme suit :<br/><br/>   -Chiffre nombres sont toujours interprétés comme la clé correspondante, au lieu des valeurs ASCII ou ANSI.<br/>   -Les valeurs comprises entre 1 et 26, lorsque précédé par des zéros, sont interprétées comme ^ A à ^ Z, qui représente la valeur ASCII des lettres de l’alphabet lorsque la **Ctrl** touche enfoncée.<br/>   -Les valeurs à partir du 27-32 sont toujours interprétées comme valeurs décimales à trois chiffres 027 et 032.<br/>   -Valeurs 033 à 255, précédé de 0 ou ne sont pas interprétées comme des valeurs ANSI.|
   |Un seul caractère du clavier.|Majuscules A - Z ou les nombres 0 - 9 peuvent être ASCII ou des valeurs de clé virtuels. Tout autre caractère n’est ASCII.|
   |Un caractère de clavier unique dans la plage A - Z (majuscules uniquement), précédé par un accent circonflexe (^).<br/><br/>Par exemple, ^ C.|Cette option passe à la valeur ASCII de la clé lorsqu’elle est enfoncée avec la **Ctrl** touche enfoncée.|
   |N’importe quel identificateur de clé virtuel valid.|La liste déroulante **clé** case dans la table d’accélérateurs contient une liste des identificateurs de clé virtuels standards.|

> [!NOTE]
> Lorsque vous entrez une valeur ASCII, la **modificateur** options de propriété sont limitées. La seule clé de contrôle disponible pour une utilisation est la **Alt** clé.

> [!TIP]
> Il est un raccourci pour définir une touche accélérateur à cliquer sur une entrée ou plusieurs entrées dans la table d’accélérateurs. Choisissez **enfoncée suivante** et appuyer sur les touches ou les combinaisons de touches du clavier.
>
> Le **enfoncée suivante** commande est également disponible à partir de la **modifier** menu.

#### <a name="type-property"></a>Propriété de type

Le **Type** propriété détermine si la combinaison de touches de raccourci associé de l’accélérateur **ID** est interprété comme une valeur de clé ASCII/ANSI ou une combinaison de touche virtuelle (VIRTKEY).

- Si le **Type** propriété est **ASCII**, le **modificateur** propriété peut uniquement être `None` ou `Alt`, ou il peut utiliser un accélérateur qui utilise le **Ctrl** clé (spécifié en le faisant précéder la clé avec un `^`).

- Si le **Type** propriété est **VIRTKEY**, n’importe quelle combinaison de **modificateur** et **clé** valeurs est valide.

> [!NOTE]
> Si vous souhaitez entrer une valeur dans la table d’accélérateurs et ont la valeur traitée comme ASCII/ANSI, sélectionnez le **Type** pour l’entrée dans la table et sélectionnez **ASCII** à partir de la liste déroulante. Toutefois, si vous utilisez le **enfoncée suivante** commande à partir de la **modifier** menu pour spécifier le **clé**, vous devez modifier le **Type** propriété à partir de **VIRTKEY** à **ASCII** *avant* entrer la **clé** code.

## <a name="accelerator-tables"></a>Tables d’accélérateurs

Dans un projet C++, vous pouvez modifier une table d’accélérateurs directement avec la modification sur place dans le **Éditeur d’accélérateurs**.

Les procédures ci-dessous font référence à l’utilisation des pages de propriétés standard, toutefois, la modification sur place et la méthode de page de propriété ont le même résultat. Modifications apportées à l’aide des pages de propriétés ou à l’aide de la modification sur place sont immédiatement répercutées dans la table d’accélérateurs.

Pour modifier dans une table d’accélérateurs :

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez une entrée dans la table et sélectionnez cette option pour activer la modification sur place.

1. Sélectionnez dans la zone déroulante ou tapez sur place pour apporter des modifications :

   - Pour **ID**, sélectionnez dans la liste ou d’un type à modifier.

   - Pour **modificateur**, sélectionnez dans la liste.

   - Pour **clé**, sélectionnez dans la liste ou d’un type à modifier.

   - Pour **Type**, sélectionnez **ASCII** ou **VIRTKEY** dans la liste.

Pour rechercher une entrée dans une table d’accélérateurs ouverte :

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez un en-tête de colonne pour trier le contenu de la colonne par ordre alphabétique. Par exemple, sélectionnez **ID** pour afficher tous les ID dans votre table d’accélérateurs par ordre alphabétique.

   Vous pouvez ensuite examiner la liste et rechercher l'entrée.

Pour ajouter une entrée à une table d’accélérateurs :

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Avec le bouton droit dans la table d’accélérateurs et choisissez **nouvel accélérateur** dans le menu contextuel, ou sélectionnez l’entrée de la ligne vide en bas de la table.

1. Sélectionnez un **ID** dans la liste déroulante de la **ID** boîte ou tapez un nouveau *ID* dans le **ID** boîte.

1. Type de la *clé* vous souhaitez utiliser comme accélérateur, ou avec le bouton droit et choisissez **enfoncée suivante** dans le menu contextuel pour définir une combinaison de touches, ou accédez au menu **modifier**  >  **Clé suivant typé**.

1. Modifier le **modificateur** et **Type**, si nécessaire, puis appuyez sur **entrée**.

   > [!NOTE]
   > Assurez-vous que tous les accélérateurs définis sont uniques. Vous pouvez avoir plusieurs combinaisons de touches affectées au même ID avec pas mal d’effet, par exemple, **Ctrl**+**P** et **F8** peuvent être assignées à ID_PRINT. Toutefois, avoir une combinaison de touches attribuée à plusieurs ID ne fonctionne pas correctement, par exemple, **Ctrl**+**Z** assignée à ID_SPELL_CHECK et ID_THESAURUS.

Pour supprimer une entrée à partir d’une table d’accélérateurs :

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez l’entrée que vous souhaitez supprimer, ou maintenez la **Ctrl** ou **MAJ** enfoncée tout en sélectionnant pour choisir plusieurs entrées.

1. Avec le bouton droit et choisissez **supprimer**, ou accédez au menu **modifier** > **supprimer**.

> [!TIP]
> Un raccourci pour supprimer consiste à appuyer sur la **supprimer** clé.

Pour déplacer ou copier une entrée de table d’accélérateurs vers un autre fichier de script de ressources :

1. Ouvrez les tables d’accélérateurs dans les deux fichiers de script de ressources et sélectionnez l’entrée que vous souhaitez déplacer.

1. À partir de la **modifier** menu, choisissez **copie** ou **couper**.

1. Sélectionnez une entrée dans le fichier de script de ressources cible et à partir de la **modifier** menu, choisissez **coller**.

> [!NOTE]
> Vous pouvez également utiliser les touches de raccourci pour les opérations de copie et de collage.

Pour modifier les propriétés de plusieurs touches accélérateur :

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

1. Sélectionnez les touches accélérateur que vous souhaitez modifier en maintenant enfoncée la **Ctrl** enfoncée quand vous sélectionnez chacun d’eux.

1. Accédez à la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) et tapez les valeurs que vous voulez que tous les accélérateurs sélectionnés doivent partager.

> [!NOTE]
> Chaque valeur de modificateur apparaît sous la forme d’une propriété booléenne dans la **propriétés** fenêtre. Si vous modifiez un [modificateur](../windows/accelerator-modifier-property.md) valeur dans le **propriétés** fenêtre, la table d’accélérateurs traite le nouveau modificateur comme un ajout aux modificateurs déjà présents. Pour cette raison, si vous définissez des valeurs de la modifier, vous devez définir toutes les pour vous assurer que chaque accélérateur partage les mêmes **modificateur** paramètres.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Touches accélérateur](../windows/predefined-accelerator-keys.md)<br/>