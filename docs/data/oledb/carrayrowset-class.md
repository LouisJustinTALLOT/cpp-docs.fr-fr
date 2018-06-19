---
title: CArrayRowset (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
dev_langs:
- C++
helpviewer_keywords:
- CArrayRowset class
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 691776f39c54e843cec478c3c42871e7b7e81da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091100"
---
# <a name="carrayrowset-class"></a>CArrayRowset, classe
Éléments d’accès d’un ensemble de lignes à l’aide de la syntaxe de tableau.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < class TAccessor >  
class CArrayRowset :   
   public CVirtualBuffer <TAccessor>,   
   protected CBulkRowset <TAccessor>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TAccessor`  
 Le type de classe d’accesseur que vous souhaitez que l’ensemble de lignes à utiliser.  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CArrayRowset](../../data/oledb/carrayrowset-carrayrowset.md)|Constructeur.|  
|[Instantané](../../data/oledb/carrayrowset-snapshot.md)|Lit l’ensemble de lignes en mémoire.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[(Opérateur)&#91;&#93;](../../data/oledb/carrayrowset-operator.md)|Accède à un élément de l’ensemble de lignes.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[CArrayRowset::m_nRowsRead](../../data/oledb/carrayrowset-m-nrowsread.md)|Le nombre de lignes déjà lue.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles de consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CRowset, classe](../../data/oledb/crowset-class.md)