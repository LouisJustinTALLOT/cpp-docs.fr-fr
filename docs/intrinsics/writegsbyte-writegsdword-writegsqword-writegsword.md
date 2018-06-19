---
title: __writegsbyte, __writegsdword, __writegsqword, __writegsword | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
dev_langs:
- C++
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c9eec7bb0da65bfd327726078766ab1befacbde
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328274"
---
# <a name="writegsbyte-writegsdword-writegsqword-writegsword"></a>__writegsbyte, __writegsdword, __writegsqword, __writegsword
**Section spécifique à Microsoft**  
  
 Écriture de mémoire à un emplacement spécifié par un décalage par rapport au début du segment GS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __writegsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writegsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writegsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writegsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Offset`  
 Le décalage à partir du début de GS dans lequel écrire.  
  
 [in] `Data`  
 Valeur à écrire.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__writegsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__writegsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Ces fonctions intrinsèques sont disponibles en mode noyau uniquement, et ces routines sont disponibles seulement comme fonctions intrinsèques.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)