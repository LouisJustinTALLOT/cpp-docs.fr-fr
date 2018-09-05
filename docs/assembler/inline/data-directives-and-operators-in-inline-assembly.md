---
title: Directives de données et les opérateurs dans l’Assembly Inline | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aff2f4c5ce5e7f5592aa9ec707d002c57f0eac0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678735"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Directives et opérateurs de données dans l'assembly inline

**Section spécifique à Microsoft**

Bien qu'un bloc `__asm` puisse faire référence à des types de données et des objets C ou C++, il ne peut pas définir d'objets de données avec des directives ou des opérateurs MASM. Plus précisément, vous ne pouvez pas utiliser les directives de définition **DB**, `DW`, **jj**, `DQ`, `DT`, et `DF`, ou les opérateurs `DUP` ou  **Cela**. Les structures et les enregistrements MASM ne sont pas non plus disponibles. L’assembleur inline n’accepte pas les directives `STRUC`, `RECORD`, **largeur**, ou **masque**.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>