---
description: 'En savoir plus sur : présentation des traits de fenêtre'
title: Traits des fenêtres ATL
ms.date: 11/04/2016
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
ms.openlocfilehash: a42ef66afe09e0e528f05419799dce48c43b1bbf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157293"
---
# <a name="understanding-window-traits"></a>Fonctionnement des traits de fenêtre

Les classes de traits de fenêtre fournissent une méthode simple pour standardiser les styles utilisés pour la création d’un objet fenêtre ATL. Les caractéristiques des fenêtres sont acceptées comme paramètres de modèle par [CWindowImpl](../atl/reference/cwindowimpl-class.md) et d’autres classes de fenêtre ATL pour fournir des styles de fenêtre par défaut au niveau de la classe.

Si le créateur d’une instance de fenêtre ne fournit pas explicitement de styles dans l’appel à [Create](../atl/reference/cwindowimpl-class.md#create), vous pouvez utiliser une classe de traits pour vous assurer que la fenêtre est toujours créée avec les styles corrects. Vous pouvez même vous assurer que certains styles sont définis pour toutes les instances de cette classe de fenêtre tout en autorisant la définition d’autres styles pour chaque instance.

## <a name="atl-window-traits-templates"></a>Modèles de traits de fenêtre ATL

ATL fournit deux modèles de traits de fenêtre qui vous permettent de définir des styles par défaut au moment de la compilation à l’aide de leurs paramètres de modèle.

|Classe|Description|
|-----------|-----------------|
|[CWinTraits](../atl/reference/cwintraits-class.md)|Utilisez ce modèle lorsque vous souhaitez fournir des styles de fenêtre par défaut qui seront utilisés uniquement quand aucun autre style n’est spécifié dans l’appel à `Create` . Les styles fournis au moment de l’exécution sont prioritaires sur les styles définis au moment de la compilation.|
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Utilisez cette classe lorsque vous souhaitez spécifier des styles qui doivent toujours être définis pour la classe de fenêtre. Les styles fournis au moment de l’exécution sont combinés aux styles définis au moment de la compilation à l’aide de l’opérateur de bits or.|

En plus de ces modèles, ATL fournit un certain nombre de spécialisations prédéfinies du `CWinTraits` modèle pour les combinaisons couramment utilisées de styles de fenêtre. Pour plus d’informations, consultez la documentation de référence [CWinTraits](../atl/reference/cwintraits-class.md) .

## <a name="custom-window-traits"></a>Traits de fenêtre personnalisés

Dans le cas improbable où la spécialisation de l’un des modèles fournis par ATL ne suffit pas et que vous devez créer votre propre classe de caractéristiques, vous devez simplement créer une classe qui implémente deux fonctions statiques : `GetWndStyle` et `GetWndStyleEx` :

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

Chacune de ces fonctions reçoit une valeur de style au moment de l’exécution, qu’elle peut utiliser pour produire une nouvelle valeur de style. Si votre classe de traits de fenêtre est utilisée en tant qu’argument de modèle dans une classe de fenêtre ATL, les valeurs de style passées à ces fonctions statiques sont celles passées comme arguments de style à [créer](../atl/reference/cwindowimpl-class.md#create).

## <a name="see-also"></a>Voir aussi

[classes de fenêtre](../atl/atl-window-classes.md)
