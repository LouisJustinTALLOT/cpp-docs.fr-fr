---
title: CDynamicStringAccessor, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b8888bdac7d605ce1832ef7074955fab4893b33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097596"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor, classe
Permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente de la base de données).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)|Récupère les données de la colonne spécifiée sous forme de chaîne.|  
|[setString](../../data/oledb/cdynamicstringaccessor-setstring.md)|Définit les données de la colonne spécifiée sous forme de chaîne.|  
  
## <a name="remarks"></a>Notes  
 Alors que [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) demande des données dans le format natif indiqué par le fournisseur, `CDynamicStringAccessor` demande que le fournisseur récupère toutes les données accessibles à partir du magasin de données en tant que données de type chaîne. Cela est particulièrement utile pour les tâches simples qui ne nécessitent pas de calcul de valeurs dans le magasin de données, telles que l’affichage ou l’impression du contenu du magasin de données.  
  
 Le type natif de données de la colonne dans le magasin de données n’a pas d’importance ; tant que le fournisseur peut prendre en charge la conversion de données, il fournit les données sous forme de chaîne. Si le fournisseur ne prend pas en charge la conversion du type de données natif en une chaîne (qui n’est pas courant), l’appel de demande retourne la valeur de réussite **DB_S_ERRORSOCCURED**, et l’état de la colonne correspondante indiquer un problème de conversion de **DBSTATUS_E_CANTCONVERTVALUE**.  
  
 Utilisez `CDynamicStringAccessor` méthodes pour obtenir des informations de colonne. Ces informations de colonne vous permet de créer un accesseur dynamique au moment de l’exécution.  
  
 Les informations de colonne sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenir des données à partir de la mémoire tampon à l’aide de [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md), ou stockez-le dans la mémoire tampon à l’aide de [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
 Pour une discussion et des exemples d’utilisation des classes d’accesseurs dynamiques, consultez [à l’aide d’accesseurs dynamiques](../../data/oledb/using-dynamic-accessors.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête**: atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles de consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (classe)](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor (classe)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor (classe)](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor (classe)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessorA, classe](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW, classe](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor, classe](../../data/oledb/cxmlaccessor-class.md)