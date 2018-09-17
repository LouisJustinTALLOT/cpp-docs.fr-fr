---
title: __writeeflags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writeeflags
dev_langs:
- C++
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c01e10a77278f0a02658778ec178f0a4226eb36
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704858"
---
# <a name="writeeflags"></a>__writeeflags
Écrit la valeur spécifiée dans le programme inscrivent d’état et contrôle (EFLAGS).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __writeeflags(unsigned Value);  
void __writeeflags(unsigned __int64 Value);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*Valeur*|[in] La valeur à écrire dans le Registre EFLAGS. Le `Value` paramètre est 32 bits de long pour une plateforme 32 bits et 64 bits long pour une plateforme 64 bits.|  
  
## <a name="remarks"></a>Notes  
 Ces routines sont disponibles uniquement sous forme de fonctions intrinsèques.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__writeeflags`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)