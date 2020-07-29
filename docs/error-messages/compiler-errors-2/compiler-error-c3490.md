---
title: Erreur du compilateur C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: ea7341b9c587a764c7366fa7b7c89e4fc67bc7d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230855"
---
# <a name="compiler-error-c3490"></a>Erreur du compilateur C3490

impossible de modifier 'var' car il est accessible via un objet const

Une expression lambda déclarée dans une **`const`** méthode ne peut pas modifier des données membres non mutables.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez le **`const`** modificateur de votre déclaration de méthode.

## <a name="example"></a>Exemple

L’exemple suivant génère C3490, car il modifie la variable membre `_i` dans une **`const`** méthode :

```cpp
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>Exemple

L’exemple suivant résout C3490 en supprimant le **`const`** modificateur de la déclaration de méthode :

```cpp
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>Voir aussi

[Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)
