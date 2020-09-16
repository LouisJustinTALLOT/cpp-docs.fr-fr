---
title: Erreur du compilateur C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: bdaeb8797eb71b205f737d08e74430f161cb8caa
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686546"
---
# <a name="compiler-error-c3492"></a>Erreur du compilateur C3492

'var' : vous ne pouvez pas capturer un membre d’union anonyme

Vous ne pouvez pas capturer un membre d’une union sans nom.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Donnez un nom à l’union et passez la structure d’union complète à la liste de capture de l’expression lambda.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’erreur C3492, car il capture un membre d’une union anonyme :

```cpp
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

L’exemple suivant résout l’erreur C3492 en nommant l’union et en passant la structure d’union complète à la liste de capture de l’expression lambda :

```cpp
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
