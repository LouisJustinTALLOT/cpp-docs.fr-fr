---
title: Propriété de clé d’accès rapide (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e0594e5b9e2d092330664546cbd05ccfb0060c42
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428965"
---
# <a name="accelerator-key-property-c"></a>Propriété de clé d’accès rapide (C++)

Les entrées valides pour la propriété de clé dans la table d’accélérateurs sont les suivantes :

- Entier compris entre 0 et 255 au format décimal. La valeur détermine si la valeur est traitée comme ASCII ou ANSI comme suit :

   - Chiffre nombres sont toujours interprétés comme la clé correspondante, au lieu des valeurs ASCII ou ANSI.

   - Valeurs comprises entre 1 et 26, lorsque précédé par des zéros, sont interprétées comme ^ A à ^ Z, qui représente la valeur ASCII des lettres de l’alphabet lorsque la **Ctrl** touche enfoncée.

   - Valeurs à partir du 27-32 sont toujours interprétées comme valeurs décimales à trois chiffres 027 et 032.

   - Valeurs 033 à 255, précédé de 0 ou ne sont pas interprétées comme des valeurs ANSI.

- Un seul caractère du clavier. Majuscules A - Z ou les nombres 0 - 9 peuvent être ASCII ou des valeurs de clé virtuels ; tout autre caractère n’est ASCII.

- Un caractère de clavier unique dans la plage A - Z (majuscules uniquement), précédé par un accent circonflexe (^) (par exemple, ^ C). La valeur ASCII de la clé est entré lorsqu’elle est enfoncée avec la **Ctrl** touche enfoncée.

   > [!NOTE]
   > Lorsque vous entrez une valeur ASCII, les options de propriété de modificateur sont limitées. La seule clé de contrôle disponible pour une utilisation est la **Alt** clé.

- N’importe quel identificateur de clé virtuel valid. La clé déroulante dans la table d’accélérateurs contient une liste des identificateurs de clé virtuels standards.

   > [!TIP]
   > Un autre pour définir une touche accélérateur consiste à avec le bouton droit à une entrée ou plusieurs entrées dans la table d’accélérateurs, choisissez **enfoncée suivante** dans le menu contextuel, puis appuyez sur un des serveurs cibles ou des combinaisons de touches du clavier. Le **enfoncée suivante** commande est également disponible à partir de la **modifier** menu.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Définition des propriétés d’un accélérateur](../windows/setting-accelerator-properties.md)<br/>
[Modification d’une table d’accélérateurs](../windows/editing-in-an-accelerator-table.md)<br/>
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)