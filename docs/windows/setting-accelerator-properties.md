---
title: Définition des propriétés d’un accélérateur (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb08a9dce4c90c9efddd10683bc4b7c2ac0b08b9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314415"
---
# <a name="setting-accelerator-properties"></a>Définition des propriétés d'un accélérateur

Vous pouvez définir les propriétés d’un accélérateur dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) à tout moment. Vous pouvez également utiliser le **Accelerator** éditeur pour modifier les propriétés d’un accélérateur dans la table d’accélérateurs. Modifications apportées à l’aide de la **propriétés** fenêtre ou le **Accelerator** éditeur ont le même résultat : elles sont immédiatement répercutées dans la table d’accélérateurs.

Il existe trois propriétés pour chaque ID de l’accélérateur :

- Le [propriété modificateur](../windows/accelerator-modifier-property.md) définit des combinaisons de touches pour l’accélérateur de contrôle.

   > [!NOTE]
   > Dans le **propriétés** fenêtre, cette propriété s’affiche en tant que trois propriétés booléennes distinctes, qui peuvent être contrôlées indépendamment : **Alt**, **Ctrl**et **MAJ**.

- Le [propriété de clé](../windows/accelerator-key-property.md) définit la clé réelle à utiliser comme accélérateur.

- Le [de la propriété Type](../windows/accelerator-type-property.md) détermine si la clé est interprétée comme virtuelle (VIRTKEY) ou ASCII/ANSI.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Touches accélérateur prédéfinies](../windows/predefined-accelerator-keys.md)  
[Éditeurs de ressources](../windows/resource-editors.md)  
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)