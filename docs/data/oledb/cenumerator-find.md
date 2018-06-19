---
title: CEnumerator::Find | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
dev_langs:
- C++
helpviewer_keywords:
- Find method
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2466127dab53fa6646a4f149400e4318aed59970
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094480"
---
# <a name="cenumeratorfind"></a>CEnumerator::Find
Recherche d’un nom spécifié parmi les fournisseurs disponibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 *szSearchName*  
 [in] Le nom à rechercher.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le nom a été trouvé. dans le cas contraire, **false**.  
  
## <a name="remarks"></a>Notes  
 Ce nom correspond à la **SOURCES_NAME** membre de la [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) interface.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CEnumerator, classe](../../data/oledb/cenumerator-class.md)