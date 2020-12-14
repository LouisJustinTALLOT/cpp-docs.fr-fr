---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4001'
title: Avertissement du compilateur (niveau 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: c28c1391b120983d72dc6e5b7a96faa937ee2598
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262215"
---
# <a name="compiler-warning-level-4-c4001"></a>Avertissement du compilateur (niveau 4) C4001

l’extension non standard’single line comment’a été utilisée

> [!NOTE]
> Cet avertissement est supprimé dans Visual Studio 2017 version 15,5, car les commentaires sur une seule ligne sont standard dans C99.

Les commentaires sur une seule ligne sont standard en C++ et standard en C à partir de C99.
Sous compatibilité ANSI stricte ([/za](../../build/reference/za-ze-disable-language-extensions.md)), les fichiers C qui contiennent des commentaires sur une seule ligne génèrent l’avertissement C4001 en raison de l’utilisation d’une extension non standard. Étant donné que les commentaires sur une ligne sont standard en C++, les fichiers C contenant des commentaires sur une seule ligne ne produisent pas C4001 lors de la compilation avec les extensions Microsoft (/Ze).

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
