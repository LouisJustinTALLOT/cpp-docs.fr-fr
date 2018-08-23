---
title: __writecr3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _writecr3
dev_langs:
- C++
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f2e88c7b4b19dd558a211327988dc68f81cc9d1
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540032"
---
# <a name="writecr3"></a>__writecr3
**Section spécifique à Microsoft**  
  
 Écrit la valeur `Data` au CR3 s’inscrivent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void writecr3(   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Data`  
 La valeur à écrire dans le Registre CR3.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__writecr3`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)