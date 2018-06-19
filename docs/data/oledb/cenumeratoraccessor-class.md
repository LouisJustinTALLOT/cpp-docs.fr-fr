---
title: Cenumeratoraccessor, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
dev_langs:
- C++
helpviewer_keywords:
- CEnumeratorAccessor class
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bb071f47eb7079c8de63da47ee0d837f44442c1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097239"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor, classe
Utilisé par [CEnumerator](../../data/oledb/cenumerator-class.md) pour accéder aux données à partir de l’ensemble de lignes d’énumérateur.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CEnumeratorAccessor  
```  
  
## <a name="members"></a>Membres  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|[m_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|Une variable qui indique si l’énumérateur est un énumérateur parent, si la ligne est un énumérateur.|  
|[m_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|Une variable qui indique si la ligne décrit une source de données ou d’un énumérateur.|  
|[m_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|Description de la source de données ou de l’énumérateur.|  
|[m_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|Le nom de la source de données ou de l’énumérateur.|  
|[m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|Chaîne à passer au [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) pour obtenir un moniker pour la source de données ou de l’énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Cet ensemble de lignes se compose des sources de données et les énumérateurs visibles à partir de l’énumérateur en cours.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)