---
title: __incfsbyte, __incfsword, __incfsdword | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2813fd6d06d69ee346e234b73c96b8b2e782b95b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330981"
---
# <a name="incfsbyte-incfsword-incfsdword"></a>__incfsbyte, __incfsword, __incfsdword
**Section spécifique à Microsoft**  
  
 Ajoutez-en une à la valeur à un emplacement de mémoire spécifié par un décalage par rapport au début de la `FS` segment.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __incfsbyte(   
   unsigned long Offset   
);  
void __incfsword(   
   unsigned long Offset   
);  
void __incfsdword(   
   unsigned long Offset  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Offset`  
 Le décalage à partir du début de `FS`.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__incfsbyte`|x86|  
|`__incfsword`|x86|  
|`__incfsdword`|x86|  
  
## <a name="remarks"></a>Notes  
 Ces fonctions intrinsèques sont uniquement disponibles en mode noyau, et les routines sont disponibles seulement comme fonctions intrinsèques.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__addfsbyte, \__addfsword, \__addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)   
 [__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)