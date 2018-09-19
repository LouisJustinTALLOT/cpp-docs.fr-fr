---
title: Erreur du compilateur C3920 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3920
dev_langs:
- C++
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b85638907f350eb3545a858f1319e56b2459f09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112705"
---
# <a name="compiler-error-c3920"></a>Erreur du compilateur C3920

' opérateur '' : Impossible de définir un suffixe incrémenter/décrémenter WinRT ou un opérateur CLR appelant le suffixe WinRT ou CLR postfixé entraînera l’appel le préfixe correspondant WinRT ou CLR opérateur (op_Increment/op_Decrement), mais avec la sémantique postfixée

Windows Runtime et le CLR ne prennent pas en charge l'opérateur suffixé et les opérateurs suffixés définis par l'utilisateur ne sont pas autorisés.  Vous pouvez définir un opérateur préfixé afin qu'il soit utilisé à la fois pour les opérations antérieures et postérieures à l'incrémentation.

L'exemple suivant génère l'erreur C3920 et montre comment la corriger :

```
// C3920.cpp
// compile with: /clr /LD
public value struct V {
   static V operator ++(V me, int)
   // try the following line instead
   // static V operator ++(V me)
   {   // C3920
      me.m_i++;
      return me;
   }

   int m_i;
};

```