---
title: Détermination du Type d’accesseur à utiliser | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 89a55127b8f7e5e0e7d338a9e7ba4f85e8c568d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104007"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Détermination du type d’accesseur à utiliser
Vous pouvez déterminer les types de données sur un ensemble de lignes au moment de la compilation ou au moment de l’exécution.  
  
 Si vous devez déterminer les types de données au moment de la compilation, utilisez un accesseur statique (tel que `CAccessor`). Vous pouvez déterminer les types de données manuellement ou à l’aide de l’Assistant Consommateur OLE DB ATL.  
  
 Si vous devez déterminer les types de données au moment de l’exécution, utilisez un dynamique (`CDynamicAccessor` ou ses enfants) ou l’accesseur manuel (`CManualAccessor`). Dans ce cas, vous pouvez appeler `GetColumnInfo` sur l’ensemble de lignes à retourner les informations de liaison de colonne, à partir de laquelle vous pouvez déterminer les types.  
  
 Le tableau suivant répertorie les types d’accesseurs fournis dans les modèles du consommateur. Chaque accesseur présente des avantages et inconvénients. Dans certains cas, un type d’accesseur doit répondre à vos besoins.  
  
|Classe d’accesseur|Liaison|Paramètre|Commentaire|  
|--------------------|-------------|---------------|-------------|  
|`CAccessor`|Créer un enregistrement d’utilisateur avec `COLUMN_ENTRY` macros. Les macros de lient un membre de données de cet enregistrement dans l’accesseur. Lors de la création de l’ensemble de lignes, colonnes ne peut pas être détachées.|Oui, en utilisant un **PARAM_MAP** entrée de macro. Une fois liée, ne peuvent pas être détachée.|Accesseur le plus rapide en raison de la petite quantité de code.|  
|`CDynamicAccessor`|Automatique.|Non.|Cette option est utile si vous ne connaissez pas le type de données dans un ensemble de lignes.|  
|`CDynamicParameterAccessor`|Automatique, mais peut être [substitution](../../data/oledb/overriding-a-dynamic-accessor.md).|Oui, si le fournisseur prend en charge `ICommandWithParameters`. Les paramètres liés automatiquement.|Plus lent que `CDynamicAccessor` mais utile pour l’appel des procédures stockées génériques.|  
|**CDynamicStringAccessor[A,W]**|Automatique.|Non.|Récupère les données accédées à partir du magasin de données en tant que données de type chaîne.|  
|`CManualAccessor`|À l’aide de manuel `AddBindEntry`.|Manuellement à l’aide de `AddParameterEntry`.|Très rapide. paramètres et les colonnes ne liées qu’une seule fois. Vous déterminez le type de données à utiliser. (Consultez [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) sample pour obtenir un exemple.) Nécessite plus de code que `CDynamicAccessor` ou `CAccessor`. Il est plus à l’appel direct d’OLE DB.|  
|`CXMLAccessor`|Automatique.|Non.|Récupère les données accédées à partir du magasin de données en tant que données de type chaîne et met en forme les données XML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des accesseurs](../../data/oledb/using-accessors.md)