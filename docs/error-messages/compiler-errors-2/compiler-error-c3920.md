---
description: 'En savoir plus sur : erreur du compilateur C3920'
title: Erreur du compilateur C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: b4cb793744126ee7bc91d18692d25439880fc672
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326571"
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
