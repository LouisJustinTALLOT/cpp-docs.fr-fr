---
title: CRowset (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>
- CRowset
- ATL::CRowset
- ATL::CRowset<TAccessor>
- ATL.CRowset
dev_langs:
- C++
helpviewer_keywords:
- CRowset class
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5c9a23c2e879f0d2fe1add1a970c64f6fbcc27b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098574"
---
# <a name="crowset-class"></a>CRowset, classe
Encapsule un objet d’ensemble de lignes OLE DB et plusieurs liés interfaces et fournit des méthodes de manipulation des données de l’ensemble de lignes.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TAccessor`  
 Une classe d’accesseur. La valeur par défaut est `CAccessorBase`.  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/crowset-addrefrows.md)|Incrémente le décompte de références associé à la ligne actuelle.|  
|[Fermer](../../data/oledb/crowset-close.md)|Libère les lignes et en cours `IRowset` interface.|  
|[Compare](../../data/oledb/crowset-compare.md)|Compare deux signets à l’aide de [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx).|  
|[CRowset](../../data/oledb/crowset-crowset.md)|Crée un nouveau `CRowset` de l’objet et l’associe (facultatif) une **IRowset** interface fournie en tant que paramètre.|  
|[Supprimer](../../data/oledb/crowset-delete.md)|Supprime des lignes dans l’ensemble de lignes à l’aide de [IRowsetChange:DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx).|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|Recherche la ligne correspondante suivante après le signet spécifié.|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|Retourne la position approximative d’une ligne correspondant à un signet.|  
|[GetData](../../data/oledb/crowset-getdata.md)|Récupère les données à partir de la copie de l’ensemble de lignes de la ligne.|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|Récupère les données à partir de la mémoire tampon spécifiée.|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|Récupère les données récemment extraites ou transmise à la source de données, en ignorant les modifications en attente.|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|Retourne l’état de toutes les lignes.|  
|[Insert](../../data/oledb/crowset-insert.md)|Crée et insère une nouvelle ligne à l’aide [IRowsetChange:InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx).|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|Compare la ligne spécifiée à la ligne actuelle.|  
|[MoveFirst](../../data/oledb/crowset-movefirst.md)|Repositionne l’emplacement d’extraction suivant à la position initiale.|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|Déplace vers le dernier enregistrement.|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|Extrait les données à partir de la ligne suivante de séquentielle ou un nombre spécifié de positions au-delà de la ligne suivante.|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|Se déplace vers l’enregistrement précédent.|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|Extrait la ligne marquée par un signet ou la ligne à l’offset spécifié à partir de ce signet.|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|Extrait les lignes à partir d’une position décimale dans l’ensemble de lignes.|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|Appels [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) pour libérer le handle de ligne actuelle.|  
|[SetData](../../data/oledb/crowset-setdata.md)|Définit les valeurs de données dans une ou plusieurs colonnes d’une ligne à l’aide de [IRowsetChange:SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx).|  
|[Annuler](../../data/oledb/crowset-undo.md)|Annule toutes les modifications apportées à une ligne depuis la dernière extraction ou [mise à jour](../../data/oledb/crowset-update.md).|  
|[Mettre à jour](../../data/oledb/crowset-update.md)|Transmet les modifications apportées à la ligne en cours depuis la dernière extraction ou de la mise à jour en attente.|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|Transmet les modifications apportées à toutes les lignes depuis la dernière extraction ou de la mise à jour en attente.|  
  
## <a name="remarks"></a>Notes  
 Dans OLE DB, un ensemble de lignes est l’objet par le biais duquel un programme définit et extrait les données.  
  
 Cette classe n’est pas destinée à être instanciée mais plutôt passée comme un paramètre de modèle `CTable` ou `CCommand` (`CRowset` est la valeur par défaut).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple DBVIEWER](../../visual-cpp-samples.md)   
 [Exemple multiRead](../../visual-cpp-samples.md)   
 [Attributs multiRead](../../visual-cpp-samples.md)   
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)