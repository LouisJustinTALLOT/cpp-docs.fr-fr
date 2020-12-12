---
description: 'En savoir plus sur : directives et opérateurs de données dans un assembly inline'
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
ms.openlocfilehash: a2b11aa95723245fc977f97f42b1de2f6c7306ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117950"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Directives et opérateurs de données dans l'assembly inline

**Spécifique à Microsoft**

Bien qu’un **`__asm`** bloc puisse référencer des types de données et des objets C ou C++, il ne peut pas définir d’objets de données avec des directives ou des opérateurs MASM. Plus précisément, vous ne pouvez pas utiliser les directives de définition **DB**, `DW` , **DD**, `DQ` , `DT` , et `DF` ou les opérateurs `DUP` ou.  Les structures et les enregistrements MASM ne sont pas non plus disponibles. L’assembleur inline n’accepte pas les directives `STRUC` , `RECORD` , **Width** ou **Mask**.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
