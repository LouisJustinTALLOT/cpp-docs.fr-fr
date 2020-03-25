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
ms.openlocfilehash: 865fc5fac5f46cdc8c55966e9989227d1d671d6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169251"
---
# <a name="segment-references-in-inline-assembly"></a>Références de segment dans l'assembly inline

**Section spécifique de Microsoft**

Vous devez faire référence aux segments par registre plutôt que par nom (le nom de segment `_TEXT` n'est pas valide, par exemple). Les substitutions de segments doivent utiliser le registre explicitement, comme dans ES:[BX].

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
