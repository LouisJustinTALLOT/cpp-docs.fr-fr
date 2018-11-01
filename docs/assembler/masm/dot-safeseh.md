---
title: .SAFESEH
ms.date: 08/30/2018
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: adfb9106095de3d15bafb67172b001d0f4597418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649850"
---
# <a name="safeseh"></a>.SAFESEH

Inscrit une fonction comme gestionnaire d’exceptions structuré.

## <a name="syntax"></a>Syntaxe

> . Identificateur de /SAFESEH

## <a name="remarks"></a>Notes

*identificateur* doit être l’ID pour un défini localement [PROC](../../assembler/masm/proc.md) ou [EXTRN](../../assembler/masm/extrn.md) PROC. Un [étiquette](../../assembler/masm/label-masm.md) n’est pas autorisée. La barre d’outils. SAFESEH (directive) nécessite le [/safeseh](../../assembler/masm/ml-and-ml64-command-line-reference.md) l’option de ligne de commande ml.exe.

Pour plus d’informations sur les gestionnaires d’exceptions structurées, consultez [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).

Par exemple, pour inscrire un gestionnaire d’exceptions sécurisés, créez un nouveau fichier MASM (comme suit), assembler avec /SAFESEH. et l’ajouter aux objets liés.

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>