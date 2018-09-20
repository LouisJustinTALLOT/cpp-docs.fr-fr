---
title: Ajout d’une entrée à une Table d’accélérateurs (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e0017e0c4d5462ef985b70b44120ff20066f626
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391798"
---
# <a name="adding-an-entry-to-an-accelerator-table-c"></a>Ajout d’une entrée à une Table d’accélérateurs (C++)

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Pour ajouter une entrée à une table d'accélérateurs

1. Dans un projet C++, ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Avec le bouton droit dans la table d’accélérateurs et choisissez **nouvel accélérateur** dans le menu contextuel, ou cliquez sur l’entrée de la ligne vide en bas de la table.

3. Sélectionnez un [ID](id-property.md) dans la liste déroulante dans l’ID de zone ou tapez un nouvel ID dans le **ID** boîte.

4. Type de la [clé](../windows/accelerator-key-property.md) vous souhaitez utiliser comme accélérateur, ou avec le bouton droit et choisissez **enfoncée suivante** dans le menu contextuel pour définir une combinaison de touches (la **enfoncée suivante** commande est également disponible à partir de la **modifier** menu).

5. Modifier le [modificateur](../windows/accelerator-modifier-property.md) et [Type](../windows/accelerator-type-property.md), si nécessaire.

6. Appuyez sur **Entrée**.

   > [!NOTE]
   > Assurez-vous que tous les accélérateurs définis sont uniques. Vous pouvez avoir plusieurs combinaisons de touches affectées au même ID avec pas mal d’effet, par exemple, **Ctrl** + **P** et **F8** peuvent être assignées à ID_PRINT. Toutefois, avoir une combinaison de touches attribuée à plusieurs ID ne fonctionne pas correctement, par exemple, **Ctrl** + **Z** assignée à ID_SPELL_CHECK et ID_THESAURUS.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Modification des tables d’accélérateurs](../windows/editing-accelerator-tables.md)<br/>
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)