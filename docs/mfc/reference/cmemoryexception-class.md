---
title: Classe de CMemoryException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs:
- C++
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12971af6bed7c04c6f6f214f0b583a4f7e6eb7a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366302"
---
# <a name="cmemoryexception-class"></a>Classe de CMemoryException
Représente une condition d'exception liée à une insuffisance de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMemoryException::CMemoryException](#cmemoryexception)|Construit un objet `CMemoryException`.|  
  
## <a name="remarks"></a>Notes  
 Aucune qualification supplémentaire n’est nécessaire ou possible. Mémoire des exceptions sont levées automatiquement par **nouveau**. Si vous écrivez vos propres fonctions de mémoire, à l’aide `malloc`, pour l’exemple, puis que vous êtes responsable de la lever des exceptions de mémoire.  
  
 Pour plus d’informations sur `CMemoryException`, consultez l’article [la gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  
  
##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException  
 Construit un objet `CMemoryException`.  
  
```  
CMemoryException();  
```  
  
### <a name="remarks"></a>Notes  
 N’utilisez pas ce constructeur directement, mais plutôt appeler la fonction globale [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Cette fonction globale peut parvenir à une situation d’insuffisance de mémoire, car elle construit l’objet d’exception dans la mémoire précédemment allouée. Pour plus d’informations sur le traitement des exceptions, consultez l’article [exceptions](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CException (classe)](cexception-class.md)   
 [Graphique hiérarchique](../hierarchy-chart.md)



