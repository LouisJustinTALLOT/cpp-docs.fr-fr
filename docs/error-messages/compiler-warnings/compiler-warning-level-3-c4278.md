---
title: Avertissement du compilateur (niveau 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 8c5c15105581602566116d3ed82b89a6337435c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627628"
---
# <a name="compiler-warning-level-3-c4278"></a>Avertissement du compilateur (niveau 3) C4278

> «*identificateur*' : identificateur de la bibliothèque de types '*tlb*' est déjà une macro ; utilisez le qualificateur 'rename'

Lorsque vous utilisez [#import](../../preprocessor/hash-import-directive-cpp.md), un identificateur dans la bibliothèque de types que vous importez est de déclarer un identificateur *identificateur*. Toutefois, il est déjà un symbole valide.

Utilisez le `#import` **renommer** attribut pour assigner un alias au symbole dans la bibliothèque de types.