---
title: Directives et opérateurs de données dans l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: 916dce0346bebfc5ff65ca558ae75317a187660a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169537"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Directives et opérateurs de données dans l'assembly inline

**Section spécifique de Microsoft**

Bien qu'un bloc `__asm` puisse faire référence à des types de données et des objets C ou C++, il ne peut pas définir d'objets de données avec des directives ou des opérateurs MASM. Plus précisément, vous ne pouvez pas utiliser les directives de définition **DB**, `DW`, **DD**, `DQ`, `DT`et `DF` **, ni les**opérateurs `DUP` ou. Les structures et les enregistrements MASM ne sont pas non plus disponibles. L’assembleur inline n’accepte pas les directives `STRUC`, `RECORD`, **Width**ou **Mask**.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
