---
title: Modification dans une Table d’accélérateurs (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
ms.assetid: 545b650b-4f26-4b20-8431-d942548443bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57347b88fe7d54813e06cde6d5f4b3414e79f116
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395804"
---
# <a name="editing-in-an-accelerator-table-c"></a>Modification dans une Table d’accélérateurs (C++)

### <a name="to-edit-in-an-accelerator-table"></a>Pour modifier une table d'accélérateurs

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Sélectionnez une entrée dans la table, puis cliquez pour activer la modification sur place.

3. Sélectionnez un élément dans la zone de liste déroulante fixe, ou tapez sur place pour apporter des modifications.

   - Pour [ID](id-property.md), sélectionnez dans la liste ou d’un type à modifier.

   - Pour [modificateur](../windows/accelerator-modifier-property.md), sélectionnez dans la liste.

   - Pour [clé](../windows/accelerator-key-property.md), sélectionnez dans la liste ou d’un type à modifier.

   - Pour [Type](../windows/accelerator-type-property.md), sélectionnez **ASCII** ou **VIRTKEY** dans la liste.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Modification des tables d’accélérateurs](../windows/editing-accelerator-tables.md)<br/>
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)