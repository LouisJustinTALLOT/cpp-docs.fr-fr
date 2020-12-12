---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4324'
title: Avertissement du compilateur (niveau 4) C4324
ms.date: 11/04/2016
f1_keywords:
- C4324
helpviewer_keywords:
- C4324
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
ms.openlocfilehash: 96554085fa63f4a4f91b954c1f32960b19f1dc6c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294546"
---
# <a name="compiler-warning-level-4-c4324"></a>Avertissement du compilateur (niveau 4) C4324

'struct_name' : la structure a été remplie en raison d' __declspec (align ())

Le remplissage a été ajouté à la fin d’une structure, car vous avez spécifié une valeur [__declspec (Align)](../../cpp/align-cpp.md) .

Par exemple, le code suivant génère C4324 :

```cpp
// C4324.cpp
// compile with: /W4
struct __declspec(align(32)) A
{
   char a;
};   // C4324

int main()
{
}
```
