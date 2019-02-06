---
title: Affichage des symboles des ressources (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
helpviewer_keywords:
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 4bcc06d9-7d36-486a-8a37-71da0541643c
ms.openlocfilehash: e61269261fc9172288f1edf58419009178c755d9
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763971"
---
# <a name="viewing-resource-symbols"></a>Affichage des symboles des ressources

Le **symboles des ressources** boîte de dialogue C++ vous permet d’ajouter de nouveaux symboles des ressources, changer les symboles affichés, ou passez à l’emplacement dans le code source où un symbole est en cours d’utilisation.

La boîte de dialogue contient les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Nom**|Affiche le nom du symbole. Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md).|
|**Valeur**|Affiche la valeur numérique du symbole. Pour plus d’informations, consultez [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md).|
|**En cours d’utilisation**|En cas de sélection, indique que le symbole est utilisé par une ou plusieurs ressources. La ou les ressources sont répertoriées dans la zone Utilisé par.|
|**Afficher les symboles en lecture seule**|En cas de sélection, affiche les ressources en lecture seule. Par défaut, le **symboles des ressources** boîte de dialogue affiche uniquement les ressources modifiables dans votre fichier de script de ressources, mais avec cette option est sélectionnée, les ressources modifiables s’affichent en gras et les ressources en lecture seule s’affichent en texte brut.|
|**Utilisé par**|Affiche la ou les ressources à l'aide du symbole sélectionné dans la liste des symboles. Pour passer à l’éditeur pour une ressource donnée, sélectionnez la ressource dans le **Used By** , puis cliquez sur **afficher l’utilisation**. Pour plus d’informations, consultez [ouverture de l’éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md).|
|**Nouveau**|Ouvre le **nouveau symbole** boîte de dialogue qui vous permet de définir le nom et, si nécessaire, une valeur pour un nouvel identificateur de ressource symbolique. Pour plus d’informations, consultez [création de nouveaux symboles](../windows/creating-new-symbols.md).|
|**Change**|Ouvre le **modifier le symbole** boîte de dialogue qui vous permet de modifier le nom ou la valeur d’un symbole. Si le symbole est destiné à un contrôle ou une ressource en cours d'utilisation, il ne peut être modifié qu'à partir de l'éditeur de ressources correspondant. Pour plus d’informations, consultez [modification des symboles non assignés](../windows/changing-unassigned-symbols.md).|
|**Afficher l’utilisation**|Ouvre la ressource qui contient le symbole dans l'éditeur de ressources correspondant. Pour plus d’informations, consultez [ouverture de l’éditeur de ressources pour un symbole donné](../windows/opening-the-resource-editor-for-a-given-symbol.md).|

## <a name="to-view-resource-symbols"></a>Pour afficher les symboles des ressources

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Sélectionnez **symboles des ressources** dans le menu contextuel pour afficher une table de symboles des ressources dans le **symboles des ressources** boîte de dialogue.

   > [!NOTE]
   > Pour afficher les symboles prédéfinis, cochez la **afficher les symboles en lecture seule** case à cocher.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)