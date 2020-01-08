---
title: .SAFESEH
ms.date: 11/05/2019
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: 5953ad6bdf1d9d1b0070ce83dd1d764799b7440a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317563"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (MASM 32 bits)

Inscrit une fonction comme gestionnaire d’exceptions structurées. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **.**  *Identificateur* SAFESEH

## <a name="remarks"></a>Notes

L’*identificateur* doit être l’ID d’une procédure [PROC](proc.md) ou [EXTRN](extrn.md) définie localement. Une [étiquette](label-masm.md) n’est pas autorisée. La. La directive SAFESEH requiert l’option de ligne de commande [/SAFESEH](ml-and-ml64-command-line-reference.md) ml. exe.

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

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
