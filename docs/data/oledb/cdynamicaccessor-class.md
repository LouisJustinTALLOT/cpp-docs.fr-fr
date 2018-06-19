---
title: CDynamicAccessor (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a4006afa9ebdfcf95a01103d1fd97643a6b749f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098301"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor, classe
Permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente de la base de données).  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDynamicAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cdynamicaccessor-addbindentry.md)|Ajoute une entrée de liaison pour les colonnes de sortie lors de la substitution de l’accesseur par défaut.|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|Instancie et initialise le `CDynamicAccessor` objet.|  
|[Fermer](../../data/oledb/cdynamicaccessor-close.md)|Annule toutes les colonnes, libère la mémoire allouée et libère le [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) pointeur d’interface dans la classe.|  
|[GetBookmark](../../data/oledb/cdynamicaccessor-getbookmark.md)|Récupère le signet pour la ligne actuelle.|  
|[GetBlobHandling](../../data/oledb/cdynamicaccessor-getblobhandling.md)|Récupère l’objet BLOB de valeur de la ligne en cours de traitement.|  
|[GetBlobSizeLimit](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|Récupère la taille d’objet BLOB maximale en octets.|  
|[GetColumnCount](../../data/oledb/cdynamicaccessor-getcolumncount.md)|Récupère le nombre de colonnes dans l’ensemble de lignes.|  
|[GetColumnFlags](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|Récupère les caractéristiques de la colonne.|  
|[GetColumnInfo](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|Récupère les métadonnées de colonne.|  
|[GetColumnName](../../data/oledb/cdynamicaccessor-getcolumnname.md)|Récupère le nom d’une colonne spécifiée.|  
|[GetColumnType](../../data/oledb/cdynamicaccessor-getcolumntype.md)|Récupère le type de données d’une colonne spécifiée.|  
|[GetLength](../../data/oledb/cdynamicaccessor-getlength.md)|Récupère la longueur maximale possible d’une colonne en octets.|  
|[GetOrdinal](../../data/oledb/cdynamicaccessor-getordinal.md)|Récupère l’index de colonne donné un nom de colonne.|  
|[GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)|Récupère l’état d’une colonne spécifiée.|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|Récupère les données à partir de la mémoire tampon.|  
|[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)|Définit l’objet BLOB de valeur de la ligne en cours de traitement.|  
|[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|Définit la taille de l’objet BLOB en octets.|  
|[SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|Définit la longueur de la colonne en octets.|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|Définit l’état d’une colonne spécifiée.|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|Stocke les données dans la mémoire tampon.|  
  
## <a name="remarks"></a>Notes  
 Utilisez `CDynamicAccessor` méthodes pour obtenir des informations de colonne telles que les noms de colonne, nombre de colonnes, type de données et ainsi de suite. Ces informations de colonne permet ensuite de créer un accesseur dynamiquement au moment de l’exécution.  
  
 Les informations de colonne sont stockées dans une mémoire tampon qui est créée et gérée par cette classe. Obtenir des données à partir de la mémoire tampon à l’aide de [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).  
  
 Pour une discussion et des exemples d’utilisation des classes d’accesseurs dynamiques, consultez [à l’aide d’accesseurs dynamiques](../../data/oledb/using-dynamic-accessors.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête**: atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles de consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (classe)](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor (classe)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor, classe](../../data/oledb/cmanualaccessor-class.md)