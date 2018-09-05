---
title: Erreur ML irrécupérable A1011 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1011
dev_langs:
- C++
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32949773b869d189516a381ca7df941760a1e4e4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690806"
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