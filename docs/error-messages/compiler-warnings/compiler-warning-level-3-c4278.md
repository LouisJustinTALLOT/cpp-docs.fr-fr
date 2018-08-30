---
title: Compilateur avertissement (niveau 3) C4278 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4278
dev_langs:
- C++
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f63337de2e14b1cb0f9d854df962ab2aa9c8014e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205779"
---
# <a name="compiler-warning-level-3-c4278"></a>Avertissement du compilateur (niveau 3) C4278

> «*identificateur*' : identificateur de la bibliothèque de types '*tlb*' est déjà une macro ; utilisez le qualificateur 'rename'

Lorsque vous utilisez [#import](../../preprocessor/hash-import-directive-cpp.md), un identificateur dans la bibliothèque de types que vous importez est de déclarer un identificateur *identificateur*. Toutefois, il est déjà un symbole valide.

Utilisez le `#import` **renommer** attribut pour assigner un alias au symbole dans la bibliothèque de types.