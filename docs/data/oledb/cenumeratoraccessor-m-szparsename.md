---
title: CEnumeratorAccessor::m_szParseName | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
dev_langs:
- C++
helpviewer_keywords:
- m_szParseName
ms.assetid: 32e826b6-0890-4db4-aa92-fc1ea3f528b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b10c5b3dcc09cba0d0e424c962f02fefe12a633
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096244"
---
# <a name="cenumeratoraccessormszparsename"></a>CEnumeratorAccessor::m_szParseName
Chaîne à passer au [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) pour obtenir un moniker pour la source de données ou de l’énumérateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
WCHAR m_szParseName[129];  
  
```  
  
## <a name="remarks"></a>Notes  
 Consultez [ISourcesRowset::GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx) dans les *de référence du programmeur OLE DB* pour plus d’informations.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CEnumeratorAccessor, classe](../../data/oledb/cenumeratoraccessor-class.md)