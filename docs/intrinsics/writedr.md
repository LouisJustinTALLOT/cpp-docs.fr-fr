---
title: __writedr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writedr
dev_langs:
- C++
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 598b95df8fd2f4dd2826fcfa1f59a7e2daa8d523
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42544479"
---
# <a name="writedr"></a>__writedr
Écrit la valeur spécifiée dans le Registre de débogage spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __writedr(unsigned DebugRegister, unsigned DebugValue);  
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `DebugRegister`  
 Un nombre entre 0 et 7 identifiant le débogage s’inscrire.  
  
 [in] `DebugValue`  
 Inscription d’une valeur à écrire dans le débogage.  
  
## <a name="remarks"></a>Notes  
 Ces fonctions intrinsèques sont disponibles uniquement en mode noyau, et les routines sont disponibles uniquement comme fonctions intrinsèques.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__writedr`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__readdr](../intrinsics/readdr.md)