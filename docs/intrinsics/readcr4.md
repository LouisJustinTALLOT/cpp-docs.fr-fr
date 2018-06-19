---
title: __readcr4 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr4
dev_langs:
- C++
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0c8290aad18fcad22dc05175f4e3d0ee329b2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322583"
---
# <a name="readcr4"></a>__readcr4
**Section spécifique à Microsoft**  
  
 Lit le Registre CR4 et retourne sa valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __readcr4(void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur dans le Registre CR4.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__readcr4`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)