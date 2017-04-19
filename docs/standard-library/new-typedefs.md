---
title: '&lt;new&gt;, typedefs | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: b652d0a1eac1615d1e1b0aed1df05d6a9ee661a3
ms.lasthandoff: 02/24/2017

---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt;, typedefs
||  
|-|  
|[new_handler](#new_handler)|  
  
##  <a name="new_handler"></a>  new_handler  
 Le type pointe vers une fonction pouvant être utilisée comme gestionnaire new.  
  
```
typedef void (*new_handler)();
```  
  
### <a name="remarks"></a>Remarques  
 Ce type de fonction de gestionnaire est appelé par **operatornew** ou `operator new[]` quand ils ne peuvent pas satisfaire à une demande de stockage supplémentaire.  
  
### <a name="example"></a>Exemple  
  Pour obtenir un exemple utilisant `new_handler` comme valeur de retour, consultez [set_new_handler](../standard-library/new-functions.md#set_new_handler).  
  
## <a name="see-also"></a>Voir aussi  
 [\<new>](../standard-library/new.md)




