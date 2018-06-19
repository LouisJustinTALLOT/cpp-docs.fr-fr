---
title: Initialisation du moteur de base de données DAO et l’arrêt | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f28c0c166bcbf13181161d6afce484fe4a45b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369900"
---
# <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO
Lorsque vous utilisez des objets DAO de MFC, le moteur de base de données DAO doit d’abord être initialisé et puis interrompue avant la fermeture de votre application ou une DLL. Deux fonctions, `AfxDaoInit` et `AfxDaoTerm`, effectuer ces tâches.  
  
### <a name="dao-database-engine-initialization-and-termination"></a>Initialisation et terminaison du moteur de base de données DAO  
  
|||  
|-|-|  
|[AfxDaoInit](#afxdaoinit)|Initialise le moteur de base de données DAO.|  
|[AfxDaoTerm](#afxdaoterm)|Arrête le moteur de base de données DAO.|  
  
##  <a name="afxdaoinit"></a>  AfxDaoInit  
 Cette fonction initialise le moteur de base de données DAO.  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>Notes  
 Dans la plupart des cas, vous n’avez pas besoin d’appeler `AfxDaoInit` , car l’application qu’il appelle automatiquement lorsqu’il est nécessaire.  
  
 Pour plus d’informations et pour obtenir un exemple de l’appel de `AfxDaoInit`, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdao.h  
  
##  <a name="afxdaoterm"></a>  AfxDaoTerm  
 Cette fonction termine le moteur de base de données DAO.  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>Notes  
 En règle générale, vous devez uniquement appeler cette fonction dans une expression régulière DLL MFC ; une application appelle automatiquement `AfxDaoTerm` lorsqu’elle est nécessaire.  
  
 Dans la DLL régulière MFC, appelez `AfxDaoTerm` avant la `ExitInstance` (fonction), mais une fois que tous les objets DAO de MFC ont été détruits.  
  
 Pour plus d’informations, consultez [Note technique 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  

### <a name="requirements"></a>Spécifications  
  **En-tête** afxdao.h  

## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
