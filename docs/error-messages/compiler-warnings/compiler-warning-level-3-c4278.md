---
title: Compilateur avertissement (niveau 3) C4278 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 7b556166f61c5d77ac34fb7243ac25d5baeaa2b1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296674"
---
# <a name="compiler-warning-level-3-c4278"></a>Avertissement du compilateur (niveau 3) C4278
'identificateur' : identificateur de la bibliothèque de types 'tlb' est déjà une macro ; Utilisez le qualificateur 'rename'  
  
 Lorsque vous utilisez [#import](../../preprocessor/hash-import-directive-cpp.md), un identificateur dans la bibliothèque de types que vous importez tente de déclarer un identificateur ***identificateur***. Toutefois, il est déjà un symbole valide.  
  
 Utilisez le `#import` **renommer** attribut pour assigner un alias au symbole dans la bibliothèque de types.