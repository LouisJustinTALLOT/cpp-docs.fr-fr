---
title: Csimplerow, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
dev_langs:
- C++
helpviewer_keywords:
- CSimpleRow class
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 68f1983eaad36494892c9a18dcb2dbebe2da1f11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099561"
---
# <a name="csimplerow-class"></a>CSimpleRow, classe
Fournit une implémentation par défaut pour le handle de ligne, qui est utilisé dans le [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) classe.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CSimpleRow  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[AddRefRow](../../data/oledb/csimplerow-addrefrow.md)|Ajoute un décompte de références à un handle de ligne existant.|  
|[Compare](../../data/oledb/csimplerow-compare.md)|Compare deux lignes pour voir s’ils font référence à la même instance de ligne.|  
|[CSimpleRow](../../data/oledb/csimplerow-csimplerow.md)|Constructeur.|  
|[ReleaseRow](../../data/oledb/csimplerow-releaserow.md)|Libère des lignes.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_dwRef](../../data/oledb/csimplerow-m-dwref.md)|Décompte de références à un handle de ligne existant.|  
|[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)|Un index à l’ensemble de lignes qui représente le curseur.|  
  
## <a name="remarks"></a>Notes  
 Un handle de ligne est logiquement une balise unique pour une ligne de résultats. `IRowsetImpl` Crée un nouveau `CSimpleRow` pour chaque ligne demandée dans [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` peut également être remplacé par votre propre implémentation de la poignée de ligne, car il s’agit d’un argument de modèle par défaut de `IRowsetImpl`. La seule exigence de remplacement de cette classe est d’avoir à la classe de remplacement de fournir un constructeur qui accepte un seul paramètre de type **LONG**.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl, classe](../../data/oledb/irowsetimpl-class.md)