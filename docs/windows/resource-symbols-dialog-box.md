---
title: Boîte de dialogue symboles de ressources (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resourcesymbols
helpviewer_keywords:
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
ms.openlocfilehash: 156b531bfcedca70c930d77773d3a308735735f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483510"
---
# <a name="resource-symbols-dialog-box-c"></a>Boîte de dialogue symboles de ressources (C++)

Le **symboles des ressources** boîte de dialogue C++ vous permet d’ajouter de nouveaux symboles des ressources, changer les symboles affichés, ou passez à l’emplacement dans le code source où un symbole est en cours d’utilisation.

- **Name**

   Affiche le nom du symbole. Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md).

- **Valeur**

   Affiche la valeur numérique du symbole. Pour plus d’informations, consultez [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md).

- **En cours d’utilisation**

   En cas de sélection, indique que le symbole est utilisé par une ou plusieurs ressources. La ou les ressources sont répertoriées dans la zone Utilisé par.

- **Afficher les symboles en lecture seule**

   En cas de sélection, affiche les ressources en lecture seule. Par défaut, le **symboles des ressources** boîte de dialogue affiche uniquement les ressources modifiables dans votre fichier de script de ressources, mais avec cette option est sélectionnée, les ressources modifiables s’affichent en gras et les ressources en lecture seule s’affichent en texte brut.

- **Utilisé par**

   Affiche la ou les ressources à l'aide du symbole sélectionné dans la liste des symboles. Pour passer à l’éditeur pour une ressource donnée, sélectionnez la ressource dans le **Used By** , puis cliquez sur **afficher l’utilisation**. Pour plus d’informations, consultez [ouverture de l’éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md).

- **Nouveau**

   Ouvre le **nouveau symbole** boîte de dialogue qui vous permet de définir le nom et, si nécessaire, une valeur pour un nouvel identificateur de ressource symbolique. Pour plus d’informations, consultez [création de nouveaux symboles](../windows/creating-new-symbols.md).

- **Modification**

   Ouvre le **modifier le symbole** boîte de dialogue qui vous permet de modifier le nom ou la valeur d’un symbole. Si le symbole est destiné à un contrôle ou une ressource en cours d'utilisation, il ne peut être modifié qu'à partir de l'éditeur de ressources correspondant. Pour plus d’informations, consultez [modification des symboles non assignés](../windows/changing-unassigned-symbols.md).

- **Afficher l’utilisation**

   Ouvre la ressource qui contient le symbole dans l'éditeur de ressources correspondant. Pour plus d’informations, consultez [ouverture de l’éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Affichage des symboles des ressources](../windows/viewing-resource-symbols.md)