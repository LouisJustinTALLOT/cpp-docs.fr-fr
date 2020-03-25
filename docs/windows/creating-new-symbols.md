---
title: 'Comment : créer des symboles (C++)'
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
ms.openlocfilehash: 1c69e8878885acd80c285691fb0861a476af03ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160513"
---
# <a name="how-to-create-symbols-c"></a>Comment : créer des symboles (C++)

Lorsque vous commencez un nouveau projet, il peut s’avérer utile de mapper les noms de symboles dont vous avez besoin avant de créer les ressources auxquelles ils seront affectés.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier. RC, consultez [Comment : créer des ressources](../windows/how-to-create-a-resource-script-file.md).

La boîte de dialogue **symboles des ressources** vous permet d’ajouter de nouveaux symboles de ressources, de modifier les symboles affichés ou d’ignorer l’emplacement dans le code source où un symbole est utilisé.

La boîte de dialogue contient les propriétés suivantes :

|Propriété|Description|
|--------------------------|------------------------------------------|
|**Nom**|Affiche le nom du symbole.<br/><br/>Pour plus d’informations, consultez [restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md).|
|**Valeur**|Affiche la valeur numérique du symbole.<br/><br/>Pour plus d’informations, consultez [restrictions relatives aux valeurs de symboles](../windows/symbol-value-restrictions.md).|
|**En cours d’utilisation**|En cas de sélection, indique que le symbole est utilisé par une ou plusieurs ressources.<br/><br/>La ou les ressources sont répertoriées dans la zone **utilisé par** .|
|**Afficher les symboles en lecture seule**|En cas de sélection, affiche les ressources en lecture seule.<br/><br/>Par défaut, la boîte de dialogue **symboles des ressources** affiche uniquement les ressources modifiables dans votre fichier de script de ressources. Toutefois, si cette option est sélectionnée, les ressources modifiables s’affichent en gras et les ressources en lecture seule s’affichent en texte brut.|
|**Utilisé par**|Affiche la ou les ressources à l'aide du symbole sélectionné dans la liste des symboles.<br/><br/>Pour accéder à l’éditeur d’une ressource donnée, sélectionnez la ressource dans la zone **utilisé par** , puis choisissez **afficher l’utilisation**.|
|**Nouveau**|Ouvre la boîte de dialogue **nouveau symbole** qui vous permet de définir le nom et, si nécessaire, une valeur pour un nouvel identificateur de ressource symbolique.|
|**Modification**|Ouvre la boîte de dialogue **modifier le symbole** qui vous permet de modifier le nom ou la valeur d’un symbole.<br/><br/>Si le symbole est destiné à un contrôle ou une ressource en cours d'utilisation, il ne peut être modifié qu'à partir de l'éditeur de ressources correspondant. Pour plus d’informations, consultez [gérer les symboles](../windows/changing-unassigned-symbols.md).|
|**Afficher l’utilisation**|Ouvre la ressource qui contient le symbole dans l'éditeur de ressources correspondant.|

## <a name="create-symbols"></a>Créer des symboles

### <a name="to-create-a-new-symbol"></a>Pour créer un symbole

1. Dans la boîte de dialogue **symboles des ressources** , choisissez **nouveau**.

1. Dans la zone **nom** , tapez un nom de symbole.

1. Acceptez la valeur de symbole assignée ou tapez une nouvelle valeur dans la zone **valeur** .

1. Sélectionnez **OK** pour ajouter le nouveau symbole à la liste des symboles.

> [!NOTE]
> Si vous tapez un nom de symbole qui existe déjà, un message s'affiche en indiquant qu'un symbole portant le même nom est déjà défini. Vous ne pouvez pas définir au moins deux symboles portant le même nom, mais vous pouvez définir des symboles différents avec la même valeur numérique.

## <a name="to-view-resource-symbols"></a>Pour afficher les symboles des ressources

Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur votre fichier *. RC* et sélectionnez **symboles des ressources** pour afficher une table de symboles de ressources dans la boîte de dialogue **symboles des ressources** .

> [!NOTE]
> Pour afficher les symboles prédéfinis, activez la case à cocher **afficher les symboles en lecture seule** .

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Pour ouvrir l’éditeur de ressources pour un symbole donné

Lorsque vous parcourez les symboles des **ressources**, vous pouvez avoir besoin d’informations supplémentaires sur l’utilisation d’un symbole particulier. Le bouton **afficher l’utilisation** offre un moyen rapide d’obtenir ces informations.

1. Dans la boîte de dialogue **symboles des ressources** , dans la zone **nom** , sélectionnez un symbole.

1. Dans la zone **utilisé par** , sélectionnez le type de ressource qui vous intéresse.

1. Sélectionnez le bouton **afficher l’utilisation** .

   La ressource s'affiche dans la fenêtre d'éditeur appropriée.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Identificateurs de ressources (symboles)](../windows/symbols-resource-identifiers.md)<br/>
[Comment : gérer des symboles](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)<br/>
