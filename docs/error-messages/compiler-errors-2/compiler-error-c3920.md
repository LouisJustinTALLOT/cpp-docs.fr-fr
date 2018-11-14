---
title: Erreur du compilateur C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: d7163cf07a440a0afd1216b3e5cf665326ffb963
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522101"
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