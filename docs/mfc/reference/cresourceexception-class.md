---
title: Classe de CResourceException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fdbfb29b00eaac40b4da2b78753df6a0596764f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371528"
---
# <a name="cresourceexception-class"></a>Classe de CResourceException
Générée lorsque Windows ne peut pas trouver ou allouer une ressource demandée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CResourceException : public CSimpleException  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CResourceException::CResourceException](#cresourceexception)|Construit un objet `CResourceException`.|  
  
## <a name="remarks"></a>Notes  
 Aucune qualification supplémentaire n’est nécessaire ou possible.  
  
 Pour plus d’informations sur l’utilisation de `CResourceException`, consultez l’article [la gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="cresourceexception"></a>  CResourceException::CResourceException  
 Construit un objet `CResourceException`.  
  
```  
CResourceException();
```  
  
### <a name="remarks"></a>Notes  
 N’utilisez pas ce constructeur directement, mais plutôt appeler la fonction globale [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Pour plus d’informations sur les exceptions, consultez l’article [la gestion des exceptions dans MFC](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CException (classe)](cexception-class.md)   
 [Graphique hiérarchique](../hierarchy-chart.md)


