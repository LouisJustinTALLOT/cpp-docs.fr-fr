---
title: SafeIntException, classe | Microsoft Docs
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
ms.openlocfilehash: a08db707afa2c307eab1dabdd0b20dad81e1a03e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016338"
---
# <a name="safeintexception-class"></a>SafeIntException, classe
Le `SafeInt` classe utilise **SafeIntException** pour identifier la raison pour laquelle une opération mathématique ne peut pas être effectuée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class SafeIntException;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
 [SafeIntException::SafeIntException](../windows/safeintexception-safeintexception.md)  
 Crée un **SafeIntException** objet.  
  
## <a name="remarks"></a>Notes  
 Le [classe SafeInt](../windows/safeint-class.md) est la seule classe qui utilise le **SafeIntException** classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [SafeIntException Class](../windows/safeintexception-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** safeint.h  
  
 **Namespace :** msl::utilities  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque SafeInt](../windows/safeint-library.md)   
 [SafeInt, classe](../windows/safeint-class.md)