---
title: Compilateur avertissement (niveau 1) C4124 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: accd58c123bcd74e54176eed5eb974c3df33dbab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279316"
---
# <a name="compiler-warning-level-1-c4124"></a>Compilateur avertissement (niveau 1) C4124
__fastcall avec contrôle de pile est inefficace  
  
 Le `__fastcall` mot clé a été utilisé avec le contrôle de pile activé.  
  
 Le `__fastcall` convention génère du code plus rapide, mais la vérification de la pile de rend le code plus lent. Lorsque vous utilisez `__fastcall`, désactiver la vérification de la pile avec les **check_stack** pragma ou/GS.  
  
 Cet avertissement est émis uniquement pour la première fonction déclarée dans ces conditions.