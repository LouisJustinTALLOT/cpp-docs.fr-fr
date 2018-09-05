---
title: . SAFESEH | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d10f3c751fe05c118203bb5eeff6c5cba6ec1c8b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693166"
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
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>