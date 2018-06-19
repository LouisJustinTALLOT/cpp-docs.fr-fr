---
title: SafeIntException, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException Class
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException class
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 961fc2f2050336469f5944f603c0db3c6291a176
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33895773"
---
# <a name="safeintexception-class"></a>SafeIntException, classe
Le `SafeInt` classe utilise `SafeIntException` pour identifier la raison pour laquelle une opération mathématique ne peut pas être exécutée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class SafeIntException;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
 [SafeIntException::SafeIntException](../windows/safeintexception-safeintexception.md)  
 Crée un objet `SafeIntException`.  
  
## <a name="remarks"></a>Notes  
 Le [SafeInt, classe](../windows/safeint-class.md) est la seule classe qui utilise le `SafeIntException` classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [SafeIntException Class](../windows/safeintexception-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** safeint.h  
  
 **Namespace :** msl::utilities  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque SafeInt](../windows/safeint-library.md)   
 [SafeInt, classe](../windows/safeint-class.md)