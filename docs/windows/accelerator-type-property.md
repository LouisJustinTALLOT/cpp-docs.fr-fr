---
title: Propriété de Type d’accélérateur (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d38d5a78eb37a028f29da430a762604b2e50d632
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315689"
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

[Définition des propriétés d’un accélérateur](../windows/setting-accelerator-properties.md)  
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)