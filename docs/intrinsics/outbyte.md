---
title: __outbyte | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outbyte
dev_langs:
- C++
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c73d32b9300a5a581306d926688230660cd998b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330621"
---
# <a name="outbyte"></a>__outbyte
**Section spécifique à Microsoft**  
  
 Génère le `out` instruction, qui envoie 1 octet spécifié par `Data` le port d’e/s spécifié par `Port`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __outbyte(   
   unsigned short Port,   
   unsigned char Data   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Port`  
 Le port pour envoyer les données.  
  
 [in] `Data`  
 Octet à être envoyé au port spécifié.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__outbyte`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)