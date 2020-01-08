---
title: XMMWORD
ms.date: 12/17/2019
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 1116729883bf9b1b9342b30332bab5de6ba59015
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75319110"
---
# <a name="xmmword"></a>XMMWORD

Utilisé pour les opérandes multimédias 128 bits avec des instructions MMX et SSE (XMM).

## <a name="syntax"></a>Syntaxe

> **XMMWORD**

## <a name="remarks"></a>Notes

**XMMWORD** est conçu pour représenter le même type que [__m128](../../cpp/m128.md).

## <a name="example"></a>Exemple

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```

## <a name="see-also"></a>Voir aussi

[Syntaxe BNF de MASM](masm-bnf-grammar.md)
