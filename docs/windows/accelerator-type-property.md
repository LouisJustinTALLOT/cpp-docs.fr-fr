---
title: Propriété de Type d’accélérateur | Microsoft Docs
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
ms.openlocfilehash: 59fae6d0809e32883d5d56e43e64525e23643d91
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602324"
---
# <a name="accelerator-type-property"></a>Type, propriété d'un accélérateur

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