---
title: Caractéristiques de fenêtre ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91ea30c79712ced6c86da0b030882fe6a88359ed
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764041"
---
# <a name="understanding-window-traits"></a>Comprendre les caractéristiques de fenêtre

Classes de traits de fenêtre fournissent une méthode simple pour standardiser les styles utilisés pour la création d’un objet de fenêtre ATL. Caractéristiques de fenêtre sont acceptés en tant que paramètres de modèle par [CWindowImpl](../atl/reference/cwindowimpl-class.md) et d’autres classes de fenêtre ATL comme un moyen de fournir des styles de fenêtre au niveau de la classe par défaut.

Si le créateur d’une instance de fenêtre ne fournit pas explicitement des styles dans l’appel à [créer](../atl/reference/cwindowimpl-class.md#create), vous pouvez utiliser une classe de traits pour vous assurer que la fenêtre est toujours créée avec les styles corrects. Vous pouvez même vous assurer que certains styles sont définis pour toutes les instances de cette classe de fenêtre tout en autorisant d’autres styles à définir sur une base par instance.

## <a name="atl-window-traits-templates"></a>Modèles de Traits de fenêtre ATL

ATL fournit deux modèles de traits de fenêtre qui vous permettent de définir des styles par défaut au moment de la compilation à l’aide de leurs paramètres de modèle.

|Classe|Description|
|-----------|-----------------|
|[CWinTraits](../atl/reference/cwintraits-class.md)|Utilisez ce modèle lorsque vous souhaitez fournir par défaut des styles de fenêtre qui seront utilisées uniquement quand aucun autre style n’est spécifiés dans l’appel à `Create`. Les styles fournis au prévalent moment de l’exécution sur les styles définis au moment de la compilation.|
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Utilisez cette classe lorsque vous souhaitez spécifier des styles qui doivent toujours être définies pour la classe de fenêtre. Les styles fournis au moment de l’exécution sont combinés avec les styles définis au moment de la compilation à l’aide de l’opérateur OR au niveau du bit.|

Outre ces modèles, ATL fournit plusieurs spécialisations prédéfinies de le `CWinTraits` modèle pour des combinaisons couramment utilisées de styles de fenêtre. Consultez le [CWinTraits](../atl/reference/cwintraits-class.md) documentation pour plus d’informations de référence.

## <a name="custom-window-traits"></a>Caractéristiques de fenêtre personnalisée

Dans le cas peu probable qu’une spécialisation des modèles fournis par ATL n’est pas suffisante et vous devez créer votre propre classe de traits, vous devez simplement créer une classe qui implémente deux fonctions statiques : `GetWndStyle` et `GetWndStyleEx`:

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

Chacune de ces fonctions recevront des valeurs de style en cours d’exécution qu’elle peut utiliser pour produire une nouvelle valeur de style. Si votre classe de traits de fenêtre est utilisé comme argument de modèle d’une classe de fenêtre ATL, les valeurs de style passées à ces fonctions statiques seront tout ce qui a été passé en tant qu’arguments de style à [créer](../atl/reference/cwindowimpl-class.md#create).

## <a name="see-also"></a>Voir aussi

[Classes de fenêtre](../atl/atl-window-classes.md)

