---
description: 'En savoir plus sur : erreur du compilateur C3121'
title: Erreur du compilateur C3121
ms.date: 11/04/2016
f1_keywords:
- C3121
helpviewer_keywords:
- C3121
ms.assetid: 1d3c7be4-d42d-4def-8d53-182c0c5cc237
ms.openlocfilehash: 62f12d17d8696e500cc21084645533825e7f25f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151058"
---
# <a name="compiler-error-c3121"></a>Erreur du compilateur C3121

Impossible de changer le GUID pour la classe’class_name'

Vous avez tenté de modifier l’ID de classe avec [__declspec (UUID)](../../cpp/uuid-cpp.md).

Par exemple, le code suivant génère C3121 :

```cpp
// C3121.cpp
[emitidl];
[module(name="MyLibrary")];

[coclass, uuid="00000000-0000-0000-0000-111111111111"]
class __declspec(uuid("00000000-0000-0000-0000-111111111112")) A   // C3121
{
};
int main()
{
}
```
