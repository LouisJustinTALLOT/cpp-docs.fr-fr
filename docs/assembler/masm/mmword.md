---
description: 'En savoir plus sur : MMWORD'
title: MMWORD
ms.date: 12/17/2019
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: f0e888efcfea7c1ca94129ff3e4cd2f40644ae13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97128231"
---
# <a name="mmword"></a>MMWORD

Utilisé pour les opérandes multimédias 64 bits avec des instructions MMX et SSE (XMM).

## <a name="syntax"></a>Syntaxe

> **MMWORD**

## <a name="remarks"></a>Notes

**MMWORD** est un type.  Avant l’ajout de **MMWORD** à MASM, des fonctionnalités équivalentes pouvaient être obtenues avec :

```asm
    mov mm0, qword ptr [ebx]
```

Bien que les deux instructions fonctionnent sur des opérandes 64 bits, **QWord** est le type des entiers non signés 64 bits et **MMWORD** est le type d’une valeur multimédia de 64 bits.

**MMWORD** est conçu pour représenter le même type que [__m64](../../cpp/m64.md).

## <a name="example"></a>Exemple

```asm
    movq     mm0, mmword ptr [ebx]
```

## <a name="see-also"></a>Voir aussi

[Syntaxe BNF de MASM](masm-bnf-grammar.md)
