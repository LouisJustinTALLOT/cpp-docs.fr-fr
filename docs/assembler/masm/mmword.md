---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: e4ebaa9d47a569bc9cf7d843d3ddb54ca5d713a0
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328225"
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