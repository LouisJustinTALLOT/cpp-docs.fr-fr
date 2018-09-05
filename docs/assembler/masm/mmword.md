---
title: MMWORD | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7314c6d0861195e312c7f72481d2e195e041965d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679232"
---
# <a name="mmword"></a>MMWORD

Utilisé pour les opérandes multimédias de 64 bits avec des instructions MMX et SSE (XMM).

## <a name="syntax"></a>Syntaxe

> MMWORD

## <a name="remarks"></a>Notes

`MMWORD` est un type.  Avant MMWORD ajouté à MASM, une fonctionnalité équivalente pourrait avoir été obtenue avec :

```asm
    mov mm0, qword ptr [ebx]
```

Bien que les deux instructions fonctionnent sur les opérandes de 64 bits, `QWORD` est de type pour les entiers non signés 64 bits et `MMWORD` est le type d’une valeur de multimédia 64 bits.

`MMWORD` est destiné à représenter le même type que [__m64](../../cpp/m64.md).

## <a name="example"></a>Exemple

```asm
    movq     mm0, mmword ptr [ebx]
```