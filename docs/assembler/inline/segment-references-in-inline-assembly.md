---
description: 'En savoir plus sur : références de segment dans un assembly inline'
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
ms.openlocfilehash: 9f9f37d7c45700358cc958f12d6f2d97da6bcf01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122081"
---
# <a name="segment-references-in-inline-assembly"></a>Références de segment dans l'assembly inline

**Spécifique à Microsoft**

Vous devez faire référence aux segments par registre plutôt que par nom (le nom de segment `_TEXT` n'est pas valide, par exemple). Les substitutions de segments doivent utiliser le registre explicitement, comme dans ES:[BX].

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
