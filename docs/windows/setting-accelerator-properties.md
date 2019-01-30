---
title: Définition des propriétés d’un accélérateur (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
ms.openlocfilehash: e1fac31635b7ccc09f9c184cf734fa4f7717cb97
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232134"
---
# <a name="setting-accelerator-properties"></a>Définition des propriétés d’un accélérateur

Vous pouvez définir les propriétés d’un accélérateur dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) à tout moment. Vous pouvez également utiliser le [Éditeur d’accélérateurs](../windows/accelerator-editor.md) pour modifier les propriétés d’un accélérateur dans la table d’accélérateurs. Modifications apportées à l’aide de la **propriétés** fenêtre ou le **Accelerator** éditeur ont le même résultat : elles sont immédiatement répercutées dans la table d’accélérateurs.

## <a name="id-property"></a>ID (propriété)

Le **ID** propriété fait référence à chaque entrée de table d’accélérateurs dans le code de programme. Cette entrée est la valeur de la commande que le programme reçoit lorsqu’un utilisateur appuie sur la touche accélérateur ou une combinaison de touches. Pour rendre un accélérateur identique à un élément de menu, que leurs ID de la même (tant que l’ID de la table d’accélérateurs est identique à l’ID de la ressource de menu).

Il existe trois propriétés pour chaque ID de l’accélérateur : le **modificateur** propriété, le **clé** propriété et le **Type** propriété.

## <a name="modifier-property"></a>Modifier (propriété)

Le **modificateur** propriété définit les combinaisons de touches pour l’accélérateur de contrôle.

> [!NOTE]
> Dans le **propriétés** fenêtre, cette propriété s’affiche en tant que distinct trois **booléenne** propriétés, qui peuvent être contrôlées indépendamment : **ALT**, **Ctrl**, et **MAJ**.

Les éléments suivants sont des entrées valides pour le **modificateur** propriété dans la table d’accélérateurs :

   |Value|Description|
   |-----------|-----------------|
   |**Aucun**|Utilisateur appuie sur uniquement le **clé** valeur. Cette valeur est utilisée plus efficacement avec les valeurs ASCII/ANSI 001 à 026, qui est interprétée comme ^ A à ^ Z (**Ctrl + A** via **Ctrl + Z**).|
   |**Alt**|L’utilisateur doit appuyer sur la **Alt** clé avant du **clé** valeur.|
   |**Ctrl**|L’utilisateur doit appuyer sur la **Ctrl** clé avant du **clé** valeur. Non valide avec le Type ASCII.|
   |**Maj**|L’utilisateur doit appuyer sur la **MAJ** clé avant du **clé** valeur.|
   |**Ctrl+Alt**|L’utilisateur doit appuyer sur le **Ctrl** clé et le **Alt** clé avant du **clé** valeur. Non valide avec le Type ASCII.|
   |**CTRL + MAJ**|L’utilisateur doit appuyer sur le **Ctrl** clé et le **MAJ** clé avant du **clé** valeur. Non valide avec le Type ASCII.|
   |**ALT + MAJ**|L’utilisateur doit appuyer sur le **Alt** clé et le **MAJ** clé avant du **clé** valeur. Non valide avec le Type ASCII.|
   |**Ctrl+Alt+Shift**|L’utilisateur doit appuyer sur **Ctrl**, **Alt**, et **MAJ** avant la **clé** valeur. Non valide avec le Type ASCII.|

## <a name="key-property"></a>Key (propriété)

Le **clé** propriété définit la clé réelle à utiliser comme accélérateur.

Les éléments suivants sont des entrées valides pour le **clé** propriété dans la table d’accélérateurs :

   |Value|Description|
   |-----------|-----------------|
   |Entier compris entre 0 et 255 au format décimal.|La valeur détermine si la valeur est traitée comme ASCII ou ANSI comme suit :<br/><br/>-Chiffre nombres sont toujours interprétés comme la clé correspondante, au lieu des valeurs ASCII ou ANSI.<br/>-Les valeurs comprises entre 1 et 26, lorsque précédé par des zéros, sont interprétées comme ^ A à ^ Z, qui représente la valeur ASCII des lettres de l’alphabet lorsque la **Ctrl** touche enfoncée.<br/>-Les valeurs à partir du 27-32 sont toujours interprétées comme valeurs décimales à trois chiffres 027 et 032.<br/>-Valeurs 033 à 255, précédé de 0 ou ne sont pas interprétées comme des valeurs ANSI.|
   |Un seul caractère du clavier.|Majuscules A - Z ou les nombres 0 - 9 peuvent être ASCII ou des valeurs de clé virtuels ; tout autre caractère n’est ASCII.|
   |Un caractère de clavier unique dans la plage A - Z (majuscules uniquement), précédé par un accent circonflexe (^) (par exemple, ^ C).|Cette option passe à la valeur ASCII de la clé lorsqu’elle est enfoncée avec la **Ctrl** touche enfoncée.|
   |N’importe quel identificateur de clé virtuel valid.|La clé déroulante dans la table d’accélérateurs contient une liste des identificateurs de clé virtuels standards.|

> [!NOTE]
> Lorsque vous entrez une valeur ASCII, les options de propriété de modificateur sont limitées. La seule clé de contrôle disponible pour une utilisation est la **Alt** clé.

> [!TIP]
> Un autre pour définir une touche accélérateur consiste à avec le bouton droit à une entrée ou plusieurs entrées dans la table d’accélérateurs, choisissez **enfoncée suivante** dans le menu contextuel, puis appuyez sur un des serveurs cibles ou des combinaisons de touches du clavier. Le **enfoncée suivante** commande est également disponible à partir de la **modifier** menu.

## <a name="type-property"></a>Type (propriété)

Le **Type** propriété détermine si la combinaison de touches de raccourci associée à l’ID de l’accélérateur est interprétée comme une valeur de clé ASCII/ANSI ou une combinaison de touche virtuelle (VIRTKEY).

- Si le **Type** propriété est ASCII, la **modificateur** propriété peut uniquement être `None` ou `Alt`, ou il peut utiliser un accélérateur qui utilise le **Ctrl** clé () spécifié en le faisant précéder la clé avec un `^`).

- Si le **Type** propriété est VIRTKEY, n’importe quelle combinaison de `Modifier` et `Key` valeurs est valide.

> [!NOTE]
> Si vous souhaitez entrer une valeur dans la table d’accélérateurs et ont la valeur soient traitées comme ASCII/ANSI, il suffit de cliquer le **Type** pour l’entrée dans la table et sélectionnez ASCII dans la liste déroulante. Toutefois, si vous utilisez le **enfoncée suivante** commande (**modifier** menu) pour spécifier le `Key`, vous devez modifier le **Type** propriété de VIRTKEY en ASCII *avant* entrer le `Key` code.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Modification d’une table d’accélérateurs](../windows/editing-in-an-accelerator-table.md)<br/>
[Touches accélérateur prédéfinies](../windows/predefined-accelerator-keys.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)<br/>
