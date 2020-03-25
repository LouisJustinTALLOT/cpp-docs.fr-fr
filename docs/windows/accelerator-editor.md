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
ms.openlocfilehash: 80ef6cc9ec956d0041c4aa3fb6a6211868cc9d73
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167561"
---
# <a name="accelerator-editor-c"></a>Éditeur d’accélérateurs (C++)

Une table d’accélérateurs C++ est une ressource Windows qui contient une liste de touches accélérateur, appelées touches de raccourci, et les identificateurs de commande qui leur sont associés. Un programme peut avoir plusieurs tables d’accélérateurs.

Normalement, les accélérateurs sont utilisés comme raccourcis clavier pour des commandes de programme qui sont également disponibles dans un menu ou une barre d’outils. Toutefois, vous pouvez utiliser la table d’accélérateurs pour définir des combinaisons de touches pour des commandes qui ne sont associées à aucun objet d’interface utilisateur.

> [!TIP]
> Lorsque vous utilisez l' **éditeur d’accélérateurs**, cliquez avec le bouton droit pour afficher un menu contextuel de commandes fréquentes. Les commandes disponibles varient selon la cible du pointeur.

Vous pouvez utiliser [Affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) pour raccorder des commandes de touches accélérateur à du code. Pour obtenir la liste des touches accélérateur prédéfinies, consultez [touches accélérateur](../windows/predefined-accelerator-keys.md).

> [!NOTE]
> Windows ne vous permet pas de créer des tables d’accélérateurs vides. Si vous créez une table d’accélérateurs sans entrée, elle est supprimée automatiquement lorsque vous l’enregistrez.

## <a name="accelerator-properties"></a>Propriétés de l’accélérateur

Vous pouvez définir des propriétés d’accélérateur dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) à tout moment. Vous pouvez également utiliser l' **éditeur d’accélérateurs** pour modifier les propriétés d’accélérateur dans la table d’accélérateurs. Les modifications apportées à l’aide de la fenêtre **Propriétés** ou de l' **éditeur d’accélérateurs** ont le même résultat, les modifications sont immédiatement reflétées dans la table d’accélérateurs.

La propriété **ID** fait référence à chaque entrée de table d’accélérateurs dans le code de programme. Cette entrée est la valeur de commande que le programme reçoit lorsqu’un utilisateur appuie sur la touche accélérateur ou sur une combinaison de touches. Pour rendre un accélérateur identique à un élément de menu, définissez l' **ID** de la même manière, tant que l' **ID** de la table d’accélérateurs est identique à l' **ID** de la ressource de menu.

Chaque **ID** d’accélérateur a trois propriétés : **modifier**, **clé**et **type**

La propriété de **modificateur** définit des combinaisons de touches de contrôle pour l’accélérateur.

> [!NOTE]
> Dans la **fenêtre Propriétés** , la propriété **modifier** apparaît sous la forme de trois propriétés **booléennes** distinctes, qui peuvent toutes être contrôlées indépendamment : **ALT**, **CTRL**et **MAJ**.

Les éléments suivants sont des entrées légales pour la propriété de **modificateur** dans la table d’accélérateurs :

   |Valeur|Description|
   |-----------|-----------------|
   |**Aucun**|L’utilisateur appuie uniquement sur la valeur de **clé** .<br/><br/>Cette valeur est utilisée le plus efficacement avec les valeurs ASCII/ANSI 001 à 026, qui est interprétée comme ^ A à ^ Z (**Ctrl + A** à **Ctrl + Z**).|
   |**Alt**|L’utilisateur doit appuyer sur **ALT** avant la valeur de la **clé** .|
   |**Ctrl**|L’utilisateur doit appuyer sur **CTRL** avant la valeur de **clé** , non valide avec le type ASCII.|
   |**Maj**|L’utilisateur doit appuyer sur **MAJ** avant la valeur de **clé** .|
   |**Ctrl + Alt**|L’utilisateur doit appuyer sur **CTRL** et **ALT** avant la valeur de **clé** , non valide avec le type ASCII.|
   |**Ctrl + Maj**|L’utilisateur doit appuyer sur **CTRL** et **MAJ** avant la valeur de **clé** , non valide avec le type ASCII.|
   |**Alt + Maj**|L’utilisateur doit appuyer sur **ALT** et **MAJ** avant la valeur de **clé** , non valide avec le type ASCII.|
   |**Ctrl + Alt + Maj**|L’utilisateur doit appuyer sur **CTRL**, **ALT**et **MAJ** avant la valeur de **clé** , non valide avec le type ASCII.|

La propriété **Key** définit la clé réelle à utiliser comme accélérateur.

Les éléments suivants sont des entrées légales pour la propriété de **clé** dans la table d’accélérateurs :

   |Valeur|Description|
   |-----------|-----------------|
   |Entier compris entre 0 et 255 au format décimal.|La valeur détermine si la valeur est traitée comme ASCII ou ANSI comme suit :<br/><br/>   -Les nombres à un chiffre sont toujours interprétés comme la clé correspondante, plutôt que comme valeurs ASCII ou ANSI.<br/>   -Les valeurs comprises entre 1 et 26, quand elles sont précédées de zéros, sont interprétées comme ^ A à ^ Z, ce qui représente la valeur ASCII des lettres de l’alphabet quand vous appuyez sur la touche **CTRL** enfoncée.<br/>   -Les valeurs de 27-32 sont toujours interprétées comme des valeurs décimales à trois chiffres de 027 à 032.<br/>   -Les valeurs comprises entre 033 et 255, qu’elles soient précédées de 0 ou non, sont interprétées comme des valeurs ANSI.|
   |Caractère de clavier unique.|Les lettres A à Z ou les nombres 0-9 peuvent être des valeurs de clé virtuelle ou ASCII. Tout autre caractère est ASCII uniquement.|
   |Caractère de clavier unique dans la plage A-Z (en majuscules uniquement), précédé d’un signe d’insertion (^), par exemple, ^ C.|Cette option permet d’entrer la valeur ASCII de la clé lorsqu’elle est appuyée avec la touche **CTRL** enfoncée.|
   |Tout identificateur de clé virtuelle valide.|La zone de liste **déroulante** de la table d’accélérateurs contient une liste d’identificateurs de clé virtuelle standard.|

> [!NOTE]
> Lorsque vous entrez une valeur ASCII, les options de propriété de **modificateur** sont limitées. La seule touche de contrôle disponible à l’utilisation est la touche **ALT** .

> [!TIP]
> Un raccourci pour définir une touche accélérateur consiste à cliquer avec le bouton droit sur une entrée ou plusieurs entrées dans la table d’accélérateurs, puis à sélectionner **clé suivante tapée** et à appuyer sur les touches ou les combinaisons de touches du clavier.
>
> Cette commande de **clé suivante** est également disponible dans le menu **Edition** .

La propriété de **type** détermine si la combinaison de touches de raccourci associée à l' **ID** d’accélérateur est interprétée comme une valeur de clé ASCII/ANSI ou une combinaison de clé virtuelle (VIRTKEY).

- Si la propriété de **type** est **ASCII**, la propriété de **modificateur** peut uniquement être `None` ou `Alt`, ou elle peut avoir un accélérateur qui utilise la touche **CTRL** , comme spécifié en faisant précéder la clé d’un `^`.

- Si la propriété **type** est **VIRTKEY**, toute combinaison de valeurs de **modificateur** et de **clé** est valide.

> [!NOTE]
> Si vous souhaitez entrer une valeur dans la table d’accélérateurs et que la valeur est traitée en tant que ASCII/ANSI, sélectionnez le **type** de l’entrée dans la table, puis sélectionnez **ASCII** dans la liste déroulante. Toutefois, si vous utilisez la commande **clé suivante** du menu **Edition** pour spécifier la **clé**, vous devez modifier la propriété **type** de **VIRTKEY** en **ASCII** *avant* d’entrer le code **clé** .

## <a name="accelerator-tables"></a>Tables d’accélérateurs

Dans un C++ projet, vous pouvez modifier une table d’accélérateurs directement avec la modification sur place dans l' **éditeur d’accélérateurs**.

Les procédures ci-dessous font référence à l’utilisation des pages de propriétés standard ; Toutefois, la modification sur place et la méthode de page de propriétés ont le même résultat. Les modifications apportées à l’aide des pages de propriétés ou de l’édition sur place sont immédiatement reflétées dans la table d’accélérateurs.

### <a name="to-edit-in-an-accelerator-table"></a>Pour modifier une table d'accélérateurs

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez une entrée dans la table et sélectionnez cette option pour activer la modification sur place.

1. Sélectionnez dans la zone de liste déroulante ou tapez sur place pour apporter des modifications :

   - Pour **ID**, sélectionnez dans la liste ou tapez pour le modifier.

   - Pour **modifier**, sélectionnez dans la liste.

   - Pour **clé**, sélectionnez dans la liste ou tapez pour effectuer la modification.

   - Pour **type**, sélectionnez **ASCII** ou **VIRTKEY** dans la liste.

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Pour rechercher une entrée dans une table d'accélérateurs ouverte

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez un en-tête de colonne pour trier le contenu de la colonne par ordre alphabétique. Par exemple, sélectionnez **ID** pour afficher tous les ID dans votre table d’accélérateurs par ordre alphabétique.

   Vous pouvez ensuite examiner la liste et rechercher l'entrée.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Pour ajouter une entrée à une table d'accélérateurs

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Cliquez avec le bouton droit dans la table d’accélérateurs et choisissez **nouvel accélérateur**, ou sélectionnez l’entrée de ligne vide en bas de la table.

1. Sélectionnez un **ID** dans la liste déroulante de la zone **ID** ou tapez un nouvel *ID* dans la zone **ID** .

1. Tapez la *clé* que vous souhaitez utiliser comme accélérateur, ou cliquez avec le bouton droit et choisissez **clé suivante typée** pour définir une combinaison de touches, ou accédez à menu **modifier** > **clé suivante tapée**.

1. Modifiez le **modificateur** et le **type**, si nécessaire, puis appuyez sur **entrée**.

> [!NOTE]
> Assurez-vous que tous les accélérateurs définis sont uniques. Plusieurs combinaisons de touches peuvent être assignées au même ID sans effet. par exemple, la **touche Ctrl**+**P** et **F8** peuvent être assignées à ID_PRINT. Toutefois, l’utilisation d’une combinaison de touches affectée à plusieurs ID ne fonctionnera pas correctement, par exemple, **Ctrl**+**Z** affecté à la fois à ID_SPELL_CHECK et ID_THESAURUS.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Pour supprimer une entrée dans une table d'accélérateurs

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez l’entrée que vous souhaitez supprimer, ou maintenez la touche **CTRL** ou **MAJ** enfoncée tout en sélectionnant plusieurs entrées.

1. Cliquez avec le bouton droit et choisissez **supprimer**, ou accédez à menu **modifier** > **supprimer**.

> [!TIP]
> Vous pouvez également appuyer sur la touche **Suppr** pour supprimer.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Pour déplacer ou copier une entrée de table d'accélérateurs vers un autre fichier de script de ressources

1. Ouvrez les tables d’accélérateurs dans les deux fichiers de script de ressources et sélectionnez l’entrée que vous souhaitez déplacer.

1. Dans le menu **Edition** , choisissez **copier** ou **couper**.

1. Sélectionnez une entrée dans le fichier de script de ressources cible et, dans le menu **Edition** , choisissez **coller**.

> [!NOTE]
> Vous pouvez également utiliser les touches de raccourci pour les opérations de copie et de collage.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Pour modifier les propriétés de plusieurs touches accélérateur

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Sélectionnez les touches d’accès rapide que vous souhaitez modifier en maintenant la touche **CTRL** enfoncée tout en sélectionnant chacune d’elles.

1. Accédez à la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) et tapez les valeurs que vous souhaitez que tous les accélérateurs sélectionnés partagent.

> [!NOTE]
> Chaque valeur de modificateur apparaît sous la forme d’une propriété booléenne dans la fenêtre **Propriétés** . Si vous modifiez une valeur de [modificateur](../windows/accelerator-modifier-property.md) dans la fenêtre **Propriétés** , la table d’accélérateurs traite le nouveau modificateur comme un ajout à tous les modificateurs qui étaient auparavant. Pour cette raison, si vous définissez des valeurs de modificateur, vous devez les définir toutes pour vous assurer que chaque accélérateur partage les mêmes paramètres de **modificateur** .

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Touches accélérateur](../windows/predefined-accelerator-keys.md)<br/>
