---
title: Détermination du type d’accesseur à utiliser
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: 31efa36bcd61caa154cd3e4c147ad5ed8728b04c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210988"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Détermination du type d’accesseur à utiliser

Vous pouvez déterminer les types de données sur un ensemble de lignes au moment de la compilation ou au moment de l’exécution.

Si vous avez besoin de déterminer les types de données au moment de la compilation, utilisez un accesseur statique (tel que `CAccessor`).

Si vous avez besoin de déterminer les types de données au moment de l’exécution, utilisez un accesseur dynamique (`CDynamicAccessor` ou ses enfants) ou manuel (`CManualAccessor`). Dans ce cas, vous pouvez appeler `GetColumnInfo` sur l’ensemble de lignes à retourner les informations de liaison de colonne, à partir de laquelle vous pouvez déterminer les types.

Le tableau suivant répertorie les types d’accesseurs fournis dans les modèles du consommateur. Chaque accesseur possède des avantages et des inconvénients. Selon votre situation, un seul type d’accesseur devrait répondre à vos besoins.

|Classe d’accesseur|Liaison|Paramètre|Commentaire|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|Créez un enregistrement d’utilisateur avec des macros COLUMN_ENTRY. Les macros lient un membre de données dans cet enregistrement à l’accesseur. Lorsque l’ensemble de lignes est créé, les colonnes ne peuvent pas être non liées.|Oui, à l’aide d’une entrée de macro PARAM_MAP. Une fois liés, les paramètres ne peuvent pas être non liés.|L’accesseur le plus rapide en raison de la petite quantité de code.|
|`CDynamicAccessor`|Automatique.|Non.|Utile si vous ne connaissez pas le type de données dans un ensemble de lignes.|
|`CDynamicParameterAccessor`|Automatique, mais peut être [remplacé](../../data/oledb/overriding-a-dynamic-accessor.md).|Oui, si le fournisseur prend en charge `ICommandWithParameters`. Paramètres liés automatiquement.|Plus lent que `CDynamicAccessor` mais utile pour l’appel des procédures stockées génériques.|
|`CDynamicStringAccessor[A,W]`|Automatique.|Non.|Récupère les données accessibles depuis la banque de données en tant que données de chaîne.|
|`CManualAccessor`|Utilisation manuelle de `AddBindEntry`.|Utilisation manuelle de `AddParameterEntry`.|Fast : les paramètres et les colonnes liées une seule fois. Vous déterminez le type de données à utiliser. (Pour obtenir un exemple, consultez l’exemple [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .) Nécessite plus de code que `CDynamicAccessor` ou `CAccessor`. Cela ressemble davantage à appeler directement OLE DB.|
|`CXMLAccessor`|Automatique.|Non.|Récupère les données accessibles depuis la banque de données en tant que données de chaîne et les formate en tant que données avec balise XML.|

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
