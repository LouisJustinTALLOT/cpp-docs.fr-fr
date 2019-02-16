---
title: 'Procédure : Créer des symboles (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 01b810d162da4d59c2044fe02a1da5c0929d41b9
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320599"
---
# <a name="how-to-create-symbols-c"></a>Procédure : Créer des symboles (C++)

Lorsque vous commencez un nouveau projet, il peut s’avérer pratique de mapper les noms de symboles que vous avez besoin avant de créer les ressources à ce qui leur sont affectées.

Le **symboles des ressources** boîte de dialogue C++ vous permet d’ajouter de nouveaux symboles des ressources, changer les symboles affichés, ou passez à l’emplacement dans le code source où un symbole est en cours d’utilisation.

La boîte de dialogue contient les propriétés suivantes :

|Propriété|Description|
|--------------------------|------------------------------------------|
|**Name**|Affiche le nom du symbole. Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md).|
|**Valeur**|Affiche la valeur numérique du symbole. Pour plus d’informations, consultez [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md).|
|**En cours d’utilisation**|En cas de sélection, indique que le symbole est utilisé par une ou plusieurs ressources. La ou les ressources sont répertoriées dans la zone Utilisé par.|
|**Afficher les symboles en lecture seule**|En cas de sélection, affiche les ressources en lecture seule. Par défaut, le **symboles des ressources** boîte de dialogue affiche uniquement les ressources modifiables dans votre fichier de script de ressources, mais avec cette option est sélectionnée, les ressources modifiables s’affichent en gras et les ressources en lecture seule s’affichent en texte brut.|
|**Utilisé par**|Affiche la ou les ressources à l'aide du symbole sélectionné dans la liste des symboles. Pour passer à l’éditeur pour une ressource donnée, sélectionnez la ressource dans le **Used By** et sélectionnez **afficher l’utilisation**.|
|**Nouveau**|Ouvre le **nouveau symbole** boîte de dialogue qui vous permet de définir le nom et, si nécessaire, une valeur pour un nouvel identificateur de ressource symbolique.|
|**Change**|Ouvre le **modifier le symbole** boîte de dialogue qui vous permet de modifier le nom ou la valeur d’un symbole. Si le symbole est destiné à un contrôle ou une ressource en cours d'utilisation, il ne peut être modifié qu'à partir de l'éditeur de ressources correspondant. Pour plus d’informations, consultez [modification des symboles non assignés](../windows/changing-unassigned-symbols.md).|
|**Afficher l’utilisation**|Ouvre la ressource qui contient le symbole dans l'éditeur de ressources correspondant.|

## <a name="create-symbols"></a>Créer des symboles

### <a name="to-create-a-new-symbol"></a>Pour créer un nouveau symbole

1. Dans le **symboles des ressources** boîte de dialogue, sélectionnez **New**.

1. Dans le **nom** , tapez un nom de symbole.

1. Acceptez la valeur de symbole assignée ou tapez une nouvelle valeur dans le **valeur** boîte.

1. Sélectionnez **OK** pour ajouter le nouveau symbole à la liste des symboles.

> [!NOTE]
> Si vous tapez un nom de symbole qui existe déjà, un message s'affiche en indiquant qu'un symbole portant le même nom est déjà défini. Vous ne pouvez pas définir plusieurs symboles avec le même nom. Toutefois, vous pouvez définir des symboles distincts avec la même valeur numérique. Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md) et [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md).

### <a name="to-view-resource-symbols"></a>Pour afficher les symboles des ressources

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Sélectionnez **symboles des ressources** dans le menu contextuel pour afficher une table de symboles des ressources dans le **symboles des ressources** boîte de dialogue.

   > [!NOTE]
   > Pour afficher les symboles prédéfinis, cochez la **afficher les symboles en lecture seule** case à cocher.

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Pour ouvrir l’éditeur de ressources pour un symbole donné

Lorsque que vous parcourez les symboles dans le **symboles des ressources**, vous souhaiterez peut-être plus d’informations sur l’utilisation d’un symbole particulier. Le **afficher l’utilisation** bouton offre un moyen rapide pour obtenir ces informations.

#### <a name="to-move-to-the-resource-editor-where-a-symbol-is-being-used"></a>Pour passer à l'éditeur de ressources où un symbole est utilisé

1. Sélectionnez un symbole dans le **nom** zone de la **symboles des ressources** boîte de dialogue.

1. Dans le **Used By** , sélectionnez le type de ressource qui vous intéresse.

1. Sélectionnez le **afficher l’utilisation** bouton.

   La ressource s'affiche dans la fenêtre d'éditeur appropriée.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Identificateurs de ressource (symboles)](../windows/symbols-resource-identifiers.md)<br/>
[Gérer les symboles](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)<br/>