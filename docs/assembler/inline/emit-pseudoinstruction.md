---
title: _emit, pseudo-instruction | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 569e3a078109e66df7dcf5cbf314817ce0786899
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061923"
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