---
title: Erreur du compilateur C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: ab0dbe8c5595c18a01f78c22056803dce91a3f31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212837"
---
# <a name="compiler-error-c2243"></a>Erreur du compilateur C2243

La conversion 'type de conversion' de 'type1' en 'type2' existe, mais n'est pas accessible

La protection d’accès ( **`protected`** ou **`private`** ) a empêché la conversion d’un pointeur vers une classe dérivée en pointeur vers la classe de base.

L'exemple suivant génère l'erreur C2243 :

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

Les classes de base avec **`protected`** accès ou ne **`private`** sont pas accessibles aux clients de la classe dérivée. Ces niveaux de contrôle d'accès permettent d'indiquer que la classe de base est un détail d'implémentation qui doit être invisible pour les clients. Utilisez une dérivation publique si vous souhaitez que les clients de la classe dérivée aient accès à une conversion implicite d'un pointeur de la classe dérivée en pointeur vers la classe de base.
