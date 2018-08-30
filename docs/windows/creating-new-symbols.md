---
title: Création de nouveaux symboles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.creating
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- symbols, creating
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d84eef4c91442eedc830fdee836dc5d950b5eae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209588"
---
# <a name="creating-new-symbols"></a>Création de nouveaux symboles

Quand vous commencez un nouveau projet, il peut s'avérer pratique de mapper les noms de symboles dont vous avez besoin avant de créer les ressources auxquelles ils seront assignés.

### <a name="to-create-a-new-symbol-using-the-resource-symbols-dialog-box"></a>Pour créer un symbole à l'aide de la boîte de dialogue Symboles des ressources

1. Dans le [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md), choisissez **New**.

2. Dans le **nom** , tapez un nom de symbole.

3. Acceptez la valeur de symbole assignée.

   - ou -

   Dans le **valeur** , tapez une nouvelle valeur.

4. Cliquez sur **OK** pour ajouter le nouveau symbole à la liste des symboles.

Si vous tapez un nom de symbole qui existe déjà, un message s'affiche en indiquant qu'un symbole portant le même nom est déjà défini. Vous ne pouvez pas définir plusieurs symboles avec le même nom. Toutefois, vous pouvez définir des symboles distincts avec la même valeur numérique. Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md) et [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, les chaînes affichage de ressources statiques et l’assignation de ressources aux propriétés.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Affichage des symboles des ressources](../windows/viewing-resource-symbols.md)  
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)