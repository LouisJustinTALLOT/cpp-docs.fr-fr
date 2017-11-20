---
title: Cenumeratoraccessor, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
dev_langs: C++
helpviewer_keywords: CEnumeratorAccessor class
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b78307c1b8f9df1945ab2376b939db2c41b8ad23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor, classe
Utilisé par [CEnumerator](../../data/oledb/cenumerator-class.md) pour accéder aux données à partir de l’ensemble de lignes d’énumérateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
## <a name="remarks"></a>Remarques  
 Cet ensemble de lignes se compose des sources de données et les énumérateurs visibles à partir de l’énumérateur en cours.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)