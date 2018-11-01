---
title: Références de segment dans l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- references, inline assembly
- segment references in inline assembly
- inline assembly, segment references
- registers
- inline assembly, registers
- registers, inline assembly
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
ms.openlocfilehash: 5c07fa897da23a55f376a20e7588c8c8c269d1a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577331"
---
# <a name="segment-references-in-inline-assembly"></a>Références de segment dans l'assembly inline

**Section spécifique à Microsoft**

Vous devez faire référence aux segments par registre plutôt que par nom (le nom de segment `_TEXT` n'est pas valide, par exemple). Les substitutions de segments doivent utiliser le registre explicitement, comme dans ES:[BX].

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>