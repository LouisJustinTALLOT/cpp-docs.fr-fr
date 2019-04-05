---
title: Détermination du type d’accesseur à utiliser
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: 98234852d0577e581135980d6b8e525aeead5dc2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031861"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Détermination du type d’accesseur à utiliser

Vous pouvez déterminer les types de données sur un ensemble de lignes au moment de la compilation ou au moment de l’exécution.

Si vous avez besoin déterminer les types de données au moment de la compilation, utilisez un accesseur statique (tel que `CAccessor`). Vous pouvez déterminer les types de données manuellement ou en utilisant le **Assistant Consommateur OLE DB ATL**.

Si vous avez besoin déterminer les types de données au moment de l’exécution, utilisez un dynamique (`CDynamicAccessor` ou ses enfants) ou accesseur manuel (`CManualAccessor`). Dans ce cas, vous pouvez appeler `GetColumnInfo` sur l’ensemble de lignes à retourner les informations de liaison de colonne, à partir de laquelle vous pouvez déterminer les types.

Le tableau suivant répertorie les types d’accesseurs fournis dans les modèles du consommateur. Chaque accesseur présente des avantages et des inconvénients. Selon votre situation, un seul type d’accesseur doit répondre à vos besoins.

|Classe d’accesseur|Liaison|Paramètre|Commentaire|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|Créer un enregistrement d’utilisateur avec macros COLUMN_ENTRY. Les macros de lient un membre de données dans l’enregistrement à l’accesseur. Lorsque l’ensemble de lignes est créé, les colonnes ne peut pas être indépendants.|Oui, à l’aide d’une entrée de macro PARAM_MAP. Une fois liés, les paramètres ne peut pas être indépendants.|Accesseur le plus rapide en raison de la petite quantité de code.|
|`CDynamicAccessor`|Automatique.|Non.|Cette option est utile si vous ne connaissez pas le type de données dans un ensemble de lignes.|
|`CDynamicParameterAccessor`|Automatique, mais peut être [substitution](../../data/oledb/overriding-a-dynamic-accessor.md).|Oui, si le fournisseur prend en charge `ICommandWithParameters`. Paramètres liés automatiquement.|Plus lent que `CDynamicAccessor` mais utile pour l’appel des procédures stockées génériques.|
|`CDynamicStringAccessor[A,W]`|Automatique.|Non.|Récupère les données accédées à partir du magasin de données en tant que données de chaîne.|
|`CManualAccessor`|À l’aide de manuel `AddBindEntry`.|Manuellement à l’aide `AddParameterEntry`.|Fast ; paramètres et les colonnes ne liées qu’une seule fois. Vous déterminez le type de données à utiliser. (Consultez [DBVIEWER](https://github.com/Microsoft/VCSamples) exemple pour obtenir un exemple.) Nécessite plus de code que `CDynamicAccessor` ou `CAccessor`. Cela correspond davantage à l’appel OLE DB directement.|
|`CXMLAccessor`|Automatique.|Non.|Récupère les données accédées à partir du magasin de données en tant que données de type chaîne et met en forme comme données XML.|

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)