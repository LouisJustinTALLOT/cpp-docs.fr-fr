---
title: Erreur du compilateur C3277
ms.date: 11/04/2016
f1_keywords:
- C3277
helpviewer_keywords:
- C3277
ms.assetid: 8ac5f476-e30c-4879-92c6-f03cdbd74045
ms.openlocfilehash: 30dea992ae2c59ddc932395de40e9b15f30b6a20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753807"
---
# <a name="compiler-error-c3277"></a>Erreur du compilateur C3277

Impossible de définir une énumération’enum’non managée dans’type’managé

Une énumération a été définie de manière incorrecte à l’intérieur d’un type managé.

L’exemple suivant génère l’C3277 :

```cpp
// C3277a.cpp
// compile with: /clr
ref class A
{
   enum E {e1,e2};   // C3277
   // try the following line instead
   // enum class E {e1,e2};
};

int main()
{
}
```
