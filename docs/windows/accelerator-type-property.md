---
title: Propriété de Type d’accélérateur (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
ms.openlocfilehash: 00699f31b821aa508feec9ffe062d768f27ee5a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475583"
---
# <a name="accelerator-type-property-c"></a>Propriété de Type d’accélérateur (C++)

L’accélérateur **Type** propriété détermine si la combinaison de touches de raccourci associée à l’ID de l’accélérateur est une combinaison de touches virtuelle ou une valeur de clé ASCII/ANSI :

- Si le **Type** propriété est ASCII, la [modificateur](../windows/accelerator-modifier-property.md) peut uniquement être `None` ou `Alt`, ou il peut avoir un accélérateur qui utilise le **Ctrl** clé (spécifiée par précédant la clé avec un `^`).

- Si le **Type** propriété est VIRTKEY, n’importe quelle combinaison de `Modifier` et `Key` valeurs est valide.

   > [!NOTE]
   > Si vous souhaitez entrer une valeur dans la table d’accélérateurs et ont la valeur soient traitées comme ASCII/ANSI, il suffit de cliquer le **Type** pour l’entrée dans la table et sélectionnez ASCII dans la liste déroulante. Toutefois, si vous utilisez le **enfoncée suivante** commande (**modifier** menu) pour spécifier le `Key`, vous devez modifier le **Type** propriété de VIRTKEY en ASCII *avant* entrer le `Key` code.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Définition des propriétés d’un accélérateur](../windows/setting-accelerator-properties.md)<br/>
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)