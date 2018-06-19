---
title: __writedr | Documents Microsoft
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
ms.openlocfilehash: 6fab96a22dec9b4cf2914fa2c02dd973bcd7ace8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329181"
---
# <a name="writedr"></a>__writedr
Écrit la valeur spécifiée dans le Registre de débogage spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __writedr(unsigned DebugRegister, unsigned DebugValue);  
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `DebugRegister`  
 Inscription d’un nombre compris entre 0 et 7 identifiant le débogage.  
  
 [in] `DebugValue`  
 Inscription d’une valeur à écrire dans le débogage.  
  
## <a name="remarks"></a>Notes  
 Ces fonctions intrinsèques sont disponibles uniquement en mode noyau, et les routines sont disponibles seulement comme fonctions intrinsèques.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__writedr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__readdr](../intrinsics/readdr.md)