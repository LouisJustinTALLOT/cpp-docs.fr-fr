---
title: SafeIntException::SafeIntException | Microsoft Docs
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
ms.openlocfilehash: 393c424feb2a84fff85ba0efb5de7cbcaf54737c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016757"
---
# <a name="safeintexceptionsafeintexception"></a>SafeIntException::SafeIntException
Crée un **SafeIntException** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *code*  
 Une valeur de données énuméré qui décrit l’erreur qui s’est produite.  
  
## <a name="remarks"></a>Notes  
 Les valeurs possibles pour *code* sont définis dans le fichier Safeint.h. Pour plus de commodité, les valeurs possibles sont également répertoriés ici.  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** safeint.h  
  
 **Namespace :** msl::utilities  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque SafeInt](../windows/safeint-library.md)   
 [SafeIntException, classe](../windows/safeintexception-class.md)   
 [SafeInt, classe](../windows/safeint-class.md)