---
title: Erreur du compilateur C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: 416752054f7397a058329e1ee4bdaef693dd0d28
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758461"
---
# <a name="compiler-error-c3920"></a>Erreur du compilateur C3920

'opérateur' : impossible de définir un opérateur WinRT ou CLR d’incrémentation/de décrémentation postfix. l’appel de l’opérateur WinRT ou CLR du suffixe correspondant appellera l’opérateur WinRT ou CLR du préfixe correspondant (op_Increment/op_Decrement), mais avec la sémantique suffixée

Windows Runtime et le CLR ne prennent pas en charge l'opérateur suffixé et les opérateurs suffixés définis par l'utilisateur ne sont pas autorisés.  Vous pouvez définir un opérateur préfixé afin qu'il soit utilisé à la fois pour les opérations antérieures et postérieures à l'incrémentation.

L'exemple suivant génère l'erreur C3920 et montre comment la corriger :

```cpp
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
