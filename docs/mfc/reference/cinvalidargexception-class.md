---
title: Classe de CInvalidArgException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
dev_langs:
- C++
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a71802a4544ae238474a0747d879d29c69f6ba19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366747"
---
# <a name="cinvalidargexception-class"></a>Classe de CInvalidArgException
Cette classe représente une condition d’exception d’argument non valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CInvalidArgException : public CSimpleException  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|Constructeur.|  
  
## <a name="remarks"></a>Notes  
 A `CInvalidArgException` objet représente une condition d’exception argument non valide.  
  
 Pour plus d’informations sur la gestion des exceptions, consultez la [CException (classe)](../../mfc/reference/cexception-class.md) rubrique et [la gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  
  
##  <a name="cinvalidargexception"></a>  CInvalidArgException::CInvalidArgException  
 Constructeur.  
  
```  
CInvalidArgException();
```  
  
### <a name="remarks"></a>Notes  
 N’utilisez pas ce constructeur directement. Appelez la fonction globale **AfxThrowInvalidArgException**.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CSimpleException, classe](../../mfc/reference/csimpleexception-class.md)
