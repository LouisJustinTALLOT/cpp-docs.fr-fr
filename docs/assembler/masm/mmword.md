---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: d4378c1435df09f249fe7f55dabd4bd0f43f6100
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397175"
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
