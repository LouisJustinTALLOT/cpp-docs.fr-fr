---
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
dev_langs:
- C++
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00f71faa5a7b81931c8ee3fbce00ea4b7e66249b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540832"
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword
**Section spécifique à Microsoft**  
  
 Lire la mémoire à partir d’un emplacement spécifié par un décalage par rapport au début du segment GS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __readgsbyte(   
   unsigned long Offset   
);  
unsigned short __readgsword(   
   unsigned long Offset   
);  
unsigned long __readgsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readgsqword(   
   unsigned long Offset   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Offset`  
 Le décalage à partir du début de `GS` pour lire à partir de.  
  
## <a name="return-value"></a>Valeur de retour  
 Le contenu de la mémoire de l’octet, word, mot double ou mot quadruple (comme indiqué par le nom de la fonction appelée) à l’emplacement `GS:[Offset]`.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__readgsbyte`|X64|  
|`__readgsdword`|X64|  
|`__readgsqword`|X64|  
|`__readgsword`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Ces fonctions intrinsèques sont disponibles uniquement en mode noyau, et les routines sont uniquement disponibles en tant que fonctions intrinsèques.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)