---
title: Erreur ML irrécupérable A1011
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 0d8d3896f7788aa3f51605651ee1b728b0e1d60a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856850"
---
# <a name="ml-fatal-error-a1011"></a>Erreur ML irrécupérable A1011

**la directive doit être dans un bloc de contrôle**

L’assembleur a trouvé une directive de niveau supérieur où l’un n’était pas attendu. Une des directives suivantes a été trouvée :

- [. SINON](../../assembler/masm/dot-else.md) [, sans. Si](../../assembler/masm/dot-if.md)

- [. ENDIF](../../assembler/masm/dot-endif.md) sans [. Si](../../assembler/masm/dot-if.md)

- [. ENDW](../../assembler/masm/dot-endw.md) sans [. PENDANT](../../assembler/masm/dot-while.md)

- [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) sans [. RÉPÉTER](../../assembler/masm/dot-repeat.md)

- [. CONTINUER](../../assembler/masm/dot-continue.md) sans [. WHILe](../../assembler/masm/dot-while.md) ou [. RÉPÉTER](../../assembler/masm/dot-repeat.md)

- [. ARRÊTER](../../assembler/masm/dot-break.md) sans [. WHILe](../../assembler/masm/dot-while.md) ou [. RÉPÉTER](../../assembler/masm/dot-repeat.md)

- [. SINON](../../assembler/masm/dot-else.md) , `.ELSE`

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>