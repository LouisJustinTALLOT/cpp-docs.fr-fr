---
title: _emit, pseudo-instruction
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: f2a7c9c4dab97bc1aba3147b5d75f6abbdac951f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540866"
---
# <a name="emit-pseudoinstruction"></a>_emit, pseudo-instruction

**Section spécifique à Microsoft**

Le **_emit** pseudo-instruction définit un seul octet à l’emplacement actuel dans le segment de texte actuel. Le **_emit** pseudo-instruction ressemble à la [DB](../../assembler/masm/db.md) directive de MASM.

Le fragment suivant place les octets 0x4A, 0x43 et 0x4B dans le code :

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
    randasm
    }
```

> [!CAUTION]
> Si `_emit` génère des instructions qui modifient les registres et que vous compilez l'application avec les optimisations, le compilateur ne peut pas déterminer quels registres sont affectés. Par exemple, si `_emit` génère une instruction qui modifie le **rax** register, le compilateur ne sait pas que **rax** a changé. Le compilateur peut alors évaluer de façon incorrecte la valeur dans ce registre après l'exécution du code assembleur inline. Par conséquent, votre application peut présenter un comportement imprévisible lorsqu'elle s'exécute.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>