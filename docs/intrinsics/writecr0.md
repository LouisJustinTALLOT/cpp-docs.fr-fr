---
title: __writecr0 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _writecr0
dev_langs:
- C++
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68bb7ec3d89ac7fffbc2896023fbd2f1dd0584ba
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540040"
---
# <a name="writecr0"></a>__writecr0
**Section spécifique à Microsoft**  
  
 Écrit la valeur `Data` pour le registre CR0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void writecr0(   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Data`  
 La valeur à écrire dans le registre CR0.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__writecr0`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)