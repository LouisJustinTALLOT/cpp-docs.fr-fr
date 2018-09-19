---
title: Erreur du compilateur C3490 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3490
dev_langs:
- C++
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 503302d323f45b5f7c3971803fef0547ff28e0c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077696"
---
# <a name="compiler-error-c3490"></a>Erreur du compilateur C3490

impossible de modifier 'var' car il est accessible via un objet const

Une expression lambda déclarée dans une méthode `const` ne peut pas modifier des données membres non mutables.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez le modificateur `const` de votre déclaration de méthode.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3490, car il modifie la variable membre `_i` dans une méthode `const` :

```
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

L’exemple suivant corrige l’erreur C3490 en supprimant le modificateur `const` de la déclaration de méthode :

```
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