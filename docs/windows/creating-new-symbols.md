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
ms.openlocfilehash: 8bb73c1a9e8d253492a7068c444dd7ddea8417da
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026355"
---
# <a name="how-to-create-symbols-c"></a>Procédure : Créer des symboles (C++)

Lorsque vous commencez un nouveau projet, il peut s’avérer pratique de mapper les noms de symboles que vous avez besoin avant de créer les ressources à ce qui leur sont affectées.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [Comment : Créer des ressources](../windows/how-to-create-a-resource-script-file.md).

Le **symboles des ressources** boîte de dialogue vous permet d’ajouter de nouveaux symboles des ressources, changer les symboles affichés, ou passez à l’emplacement dans le code source où un symbole est en cours d’utilisation.

La boîte de dialogue contient les propriétés suivantes :

|Propriété|Description|
|--------------------------|------------------------------------------|
|**Name**|Affiche le nom du symbole.<br/><br/>Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md).|
|**Valeur**|Affiche la valeur numérique du symbole.<br/><br/>Pour plus d’informations, consultez [Restrictions de valeur de symbole](../windows/symbol-value-restrictions.md).|
|**En cours d’utilisation**|En cas de sélection, indique que le symbole est utilisé par une ou plusieurs ressources.<br/><br/>L’ou les ressources sont répertoriées dans le **utilisé par** boîte.|
|**Afficher les symboles en lecture seule**|En cas de sélection, affiche les ressources en lecture seule.<br/><br/>Par défaut, le **symboles des ressources** boîte de dialogue affiche uniquement les ressources modifiables dans votre fichier de script de ressources, mais avec cette option est sélectionnée, les ressources modifiables s’affichent en gras et les ressources en lecture seule s’affichent en texte brut.|
|**Utilisé par**|Affiche la ou les ressources à l'aide du symbole sélectionné dans la liste des symboles.<br/><br/>Pour passer à l’éditeur pour une ressource donnée, sélectionnez la ressource dans le **utilisé par** et sélectionnez **afficher l’utilisation**.|
|**Nouveau**|Ouvre le **nouveau symbole** boîte de dialogue qui vous permet de définir le nom et, si nécessaire, une valeur pour un nouvel identificateur de ressource symbolique.|
|**Changement**|Ouvre le **modifier le symbole** boîte de dialogue qui vous permet de modifier le nom ou la valeur d’un symbole.<br/><br/>Si le symbole est destiné à un contrôle ou une ressource en cours d'utilisation, il ne peut être modifié qu'à partir de l'éditeur de ressources correspondant. Pour plus d’informations, consultez [gérer les symboles](../windows/changing-unassigned-symbols.md).|
|**Afficher l’utilisation**|Ouvre la ressource qui contient le symbole dans l'éditeur de ressources correspondant.|

## <a name="create-symbols"></a>Créer des symboles

### <a name="to-create-a-new-symbol"></a>Pour créer un nouveau symbole

1. Dans le **symboles des ressources** boîte de dialogue, sélectionnez **New**.

1. Dans le **nom** , tapez un nom de symbole.

1. Acceptez la valeur de symbole assignée ou tapez une nouvelle valeur dans le **valeur** boîte.

1. Sélectionnez **OK** pour ajouter le nouveau symbole à la liste des symboles.

> [!NOTE]
> Si vous tapez un nom de symbole qui existe déjà, un message s'affiche en indiquant qu'un symbole portant le même nom est déjà défini. Vous ne pouvez pas définir deux ou plusieurs symboles avec le même nom, mais vous pouvez définir différents symboles avec la même valeur numérique.

## <a name="to-view-resource-symbols"></a>Pour afficher les symboles des ressources

Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), avec le bouton droit votre *.rc* fichier et sélectionnez **symboles des ressources** pour afficher une table de symboles des ressources dans le **symboles des ressources**boîte de dialogue.

> [!NOTE]
> Pour afficher les symboles prédéfinis, cochez la **afficher les symboles en lecture seule** case à cocher.

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Pour ouvrir l’éditeur de ressources pour un symbole donné

Lorsque que vous parcourez les symboles dans le **symboles des ressources**, vous souhaiterez peut-être plus d’informations sur l’utilisation d’un symbole particulier. Le **afficher l’utilisation** bouton offre un moyen rapide pour obtenir ces informations.

1. Dans le **symboles des ressources** boîte de dialogue dans le **nom** , sélectionnez un symbole.

1. Dans le **Used By** , sélectionnez le type de ressource qui vous intéresse.

1. Sélectionnez le **afficher l’utilisation** bouton.

   La ressource s'affiche dans la fenêtre d'éditeur appropriée.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Identificateurs de ressources (symboles)](../windows/symbols-resource-identifiers.md)<br/>
[Guide pratique pour Gérer des symboles](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)<br/>