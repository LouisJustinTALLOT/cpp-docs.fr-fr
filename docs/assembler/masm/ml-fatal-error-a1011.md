---
title: Erreur ML irrécupérable A1011
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 591755a1d7066d8251f61d2a22b9601a9ccb9dcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520196"
---
# <a name="ml-fatal-error-a1011"></a>Erreur ML irrécupérable A1011

**la directive doit être dans un bloc de contrôle**

L’assembleur trouvé une directive de haut niveau où un n’était pas attendu. Une des directives suivantes a été trouvée :

- [. AUTRE](../../assembler/masm/dot-else.md) sans [. IF](../../assembler/masm/dot-if.md)

- [. ENDIF](../../assembler/masm/dot-endif.md) sans [. IF](../../assembler/masm/dot-if.md)

- [. ENDW](../../assembler/masm/dot-endw.md) sans [. WHILE](../../assembler/masm/dot-while.md)

- [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) sans [. RÉPÉTEZ](../../assembler/masm/dot-repeat.md)

- [. CONTINUER](../../assembler/masm/dot-continue.md) sans [. Bien que](../../assembler/masm/dot-while.md) ou [. RÉPÉTEZ](../../assembler/masm/dot-repeat.md)

- [. ARRÊTER](../../assembler/masm/dot-break.md) sans [. Bien que](../../assembler/masm/dot-while.md) ou [. RÉPÉTEZ](../../assembler/masm/dot-repeat.md)

- [. AUTRE](../../assembler/masm/dot-else.md) suivant `.ELSE`

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>