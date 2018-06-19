---
title: _emit, pseudo-instruction | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- _emit
dev_langs:
- C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ad75f4abf2e86cb08ba646e50e9390650993d05
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050696"
---
# <a name="emit-pseudoinstruction"></a>_emit, pseudo-instruction
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Le **_emit** _emit définit un seul octet à l’emplacement actuel dans le segment de texte actuelle. Le **_emit** _emit ressemble à la [DB](../../assembler/masm/db.md) directive MASM.  
  
 Le fragment suivant place les octets 0x4A, 0x43 et 0x4B dans le code :  
  
```  
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B  
 .  
 .  
 .  
__asm {  
     randasm  
     }  
```  
  
> [!CAUTION]
>  Si `_emit` génère des instructions qui modifient les registres et que vous compilez l'application avec les optimisations, le compilateur ne peut pas déterminer quels registres sont affectés. Par exemple, si `_emit` génère une instruction modifie le **rax** register, le compilateur ne sait pas que **rax** a changé. Le compilateur peut alors évaluer de façon incorrecte la valeur dans ce registre après l'exécution du code assembleur inline. Par conséquent, votre application peut présenter un comportement imprévisible lorsqu'elle s'exécute.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)