---
description: En savoir plus sur :. SAFESEH (MASM 32 bits)
title: .SAFESEH
ms.date: 11/05/2019
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: f0b44477d20aa024689df5e2901cc3e179596a79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97131207"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (MASM 32 bits)

Inscrit une fonction comme gestionnaire d’exceptions structurées. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **.** *Identificateur* SAFESEH

## <a name="remarks"></a>Notes

l' *identificateur* doit être l’ID d’une procédure EXTRN [ou](proc.md) d' [](extrn.md) un processus défini localement. Une [étiquette](label-masm.md) n’est pas autorisée. La. La directive SAFESEH requiert l’option de ligne de commande [/safeseh](ml-and-ml64-command-line-reference.md) ml.exe.

Pour plus d’informations sur les gestionnaires d’exceptions structurés, consultez [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).

Par exemple, pour inscrire un gestionnaire d’exceptions sécurisées, créez un nouveau fichier MASM (comme suit), assemblez avec/SafeSEH, puis ajoutez-le aux objets liés.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
