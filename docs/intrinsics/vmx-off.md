---
title: __vmx_off | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_off
dev_langs:
- C++
helpviewer_keywords:
- VMXOFF instruction
- __vmx_off intrinsic
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82d94d1cd08d08a57cedf3709d18a46639e56925
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335404"
---
# <a name="vmxoff"></a>__vmx_off
**Section spécifique à Microsoft**  
  
 Désactive l’opération extensions (VMX) dans le processeur de la machine virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __vmx_off();  
```  
  
## <a name="remarks"></a>Notes  
 Le `__vmx_off` fonction est équivalente à la `VMXOFF` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel virtualisation technique spécification pour l’Architecture IA-32 Intel, » document numéro est C97063-002, sur le [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) site.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__vmx_off`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)