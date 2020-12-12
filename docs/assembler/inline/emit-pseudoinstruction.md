---
description: 'En savoir plus sur : _emit Emit'
title: _emit, pseudo-instruction
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: d3e2a39312c94ff0e4868bed9afa74011051a129
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117807"
---
# <a name="_emit-pseudoinstruction"></a>_emit, pseudo-instruction

**Spécifique à Microsoft**

Le **_emit** Emit définit un octet à l’emplacement actuel dans le segment de texte actuel. Le **_emit** Emit ressemble à la directive [DB](../../assembler/masm/db.md) de MASM.

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
> Si `_emit` génère des instructions qui modifient les registres et que vous compilez l'application avec les optimisations, le compilateur ne peut pas déterminer quels registres sont affectés. Par exemple, si `_emit` génère une instruction qui modifie le Registre **Rax** , le compilateur ne sait pas que **Rax** a changé. Le compilateur peut alors évaluer de façon incorrecte la valeur dans ce registre après l'exécution du code assembleur inline. Par conséquent, votre application peut présenter un comportement imprévisible lorsqu'elle s'exécute.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
