---
title: Modification ou suppression des symboles non assignés
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.unassigned
helpviewer_keywords:
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
ms.assetid: b6abee4a-3c24-4697-a166-fe6a86cad35f
ms.openlocfilehash: 47cc3d7a387092afe77fdbcf4bbdb6d085eeda25
ms.sourcegitcommit: 966e4466f10c93fc12faf33d28e03b39489423fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987012"
---
# <a name="changing-or-deleting-unassigned-symbols"></a>Modification ou suppression des symboles non assignés

Lorsque vous êtes dans le [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md), vous pouvez modifier ou supprimer les symboles existants qui ne sont pas déjà affectés à une ressource ou un objet.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

## <a name="to-change-an-unassigned-symbol"></a>Pour modifier un symbole non assigné

1. Dans le **nom** zone, sélectionnez le symbole non assigné et choisissez **modification**.

1. Modifier le nom du symbole ou une valeur dans les zones fournies dans le **modifier le symbole** boîte de dialogue.

   > [!NOTE]
   > Pour changer un symbole qui *est* affecté à une ressource ou un objet, vous devez utiliser l’éditeur de ressources ou **propriétés** fenêtre. Pour plus d’informations, consultez [modification d’un symbole ou un nom de symbole](../windows/changing-a-symbol-or-symbol-name-id.md).

## <a name="to-delete-an-unassigned-unused-symbol"></a>Pour supprimer un symbole non assigné (non utilisé)

Dans le [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md), sélectionnez le symbole que vous souhaitez supprimer, puis choisissez **supprimer**.

   > [!NOTE]
   > Avant de supprimer un symbole inutilisé dans un fichier de ressources, assurez-vous qu'il n'est pas utilisé ailleurs dans le programme, ni par les fichiers de ressources inclus au moment de la compilation.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Affichage des symboles des ressources](../windows/viewing-resource-symbols.md)<br/>
[Restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md)<br/>
[Restrictions relatives à la valeur d’un symbole](../windows/symbol-value-restrictions.md)<br/>
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)