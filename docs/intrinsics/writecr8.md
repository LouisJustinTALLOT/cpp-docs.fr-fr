---
title: __writecr8 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _writecr8
dev_langs:
- C++
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3fa5bda2af8d6d6d95474743725c399d3ef5269
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538683"
---
# <a name="writecr8"></a>__writecr8
**Section spécifique à Microsoft**  
  
 Écrit la valeur `Data` au CR8 s’inscrivent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void writecr8(   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Data`  
 La valeur à écrire dans le Registre CR8.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__writecr8`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)