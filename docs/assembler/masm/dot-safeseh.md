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
ms.openlocfilehash: df9798800da293e5e0b4f545a8442380b7ff9408
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397996"
---
# <a name="safeseh-32-bit-masm"></a>. SAFESEH (MASM 32 bits)

Inscrit une fonction comme gestionnaire d’exceptions structurées. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **.**  *Identificateur* SAFESEH

## <a name="remarks"></a>Notes

L’*identificateur* doit être l’ID d’une procédure [PROC](../../assembler/masm/proc.md) ou [EXTRN](../../assembler/masm/extrn.md) définie localement. Une [étiquette](../../assembler/masm/label-masm.md) n’est pas autorisée. La. La directive SAFESEH requiert l’option de ligne de commande [/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml. exe.

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

[Informations de référence sur les directives](directives-reference.md)
