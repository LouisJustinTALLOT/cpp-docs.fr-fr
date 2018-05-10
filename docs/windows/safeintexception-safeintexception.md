---
title: SafeIntException::SafeIntException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException, constructor
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ef3c1d11c0f814699ca1492f7ec1fb49c43c3d76
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
Crée un objet `SafeIntException`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `code`  
 Une valeur de données énuméré qui décrit l’erreur qui s’est produite.  
  
## <a name="remarks"></a>Notes  
 Les valeurs possibles pour `code` sont définis dans le fichier Safeint.h. Pour plus de commodité, les valeurs possibles sont également répertoriés ici.  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** safeint.h  
  
 **Namespace :** msl::utilities  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque SafeInt](../windows/safeint-library.md)   
 [SafeIntException, classe](../windows/safeintexception-class.md)   
 [SafeInt, classe](../windows/safeint-class.md)