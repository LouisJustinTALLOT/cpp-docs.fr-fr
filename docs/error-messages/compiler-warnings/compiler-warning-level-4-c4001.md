---
title: Avertissement du compilateur (niveau 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: fc4ae55c5d25719e930a7435e0f9bf3ee2071a21
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541624"
---
# <a name="compiler-warning-level-4-c4001"></a>Avertissement du compilateur (niveau 4) C4001

l’extension non standard’single line comment’a été utilisée

> [!NOTE]
> Cet avertissement est supprimé dans Visual Studio 2017 version 15,5, car les commentaires sur une seule ligne sont standard dans C99.

Les commentaires sur une seule ligne sont C++ standard in et standard in C à partir de C99.
Sous compatibilité ANSI stricte ([/za](../../build/reference/za-ze-disable-language-extensions.md)), les fichiers C qui contiennent des commentaires sur une seule ligne génèrent l’avertissement C4001 en raison de l’utilisation d’une extension non standard. Étant donné que les commentaires sur une seule C++ligne sont standard dans, les fichiers C contenant des commentaires sur une seule ligne ne produisent pas C4001 lors de la compilation avec les extensions Microsoft (/Ze).

## <a name="example"></a>Exemple

Pour désactiver l’avertissement, supprimez les marques de commentaire [#pragma avertissement (désactiver : 4001)](../../preprocessor/warning.md).

```cpp
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```