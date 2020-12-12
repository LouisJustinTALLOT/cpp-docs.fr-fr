---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4917'
title: Avertissement du compilateur (niveau 1) C4917
ms.date: 11/04/2016
f1_keywords:
- C4917
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
ms.openlocfilehash: b85d9dced285eade22cf6b8ff61657cd53703b88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291426"
---
# <a name="compiler-warning-level-1-c4917"></a>Avertissement du compilateur (niveau 1) C4917

'déclarateur' : un GUID ne peut être associé qu’à une classe, une interface ou un espace de noms

Une structure définie par l’utilisateur autre que la [classe](../../cpp/class-cpp.md), l' [interface](../../cpp/interface.md)ou l' [espace de noms](../../cpp/namespaces-cpp.md) ne peut pas avoir de GUID.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L’exemple de code suivant génère l’erreur C4917 :

```cpp
// C4917.cpp
// compile with: /W1
#pragma warning(default : 4917)
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S
{
} s;   // C4917, don't put uuid on a struct

int main()
{
}
```
