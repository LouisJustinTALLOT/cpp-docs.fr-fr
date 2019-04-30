---
title: Compilateur avertissement (niveau 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: dd18dc27ee13eab05ea0253c8ebcc990105c15c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401486"
---
# <a name="compiler-warning-level-4-c4001"></a>Compilateur avertissement (niveau 4) C4001

extension non standard 'commentaire sur une ligne unique' a été utilisée.

> [!NOTE]
> Cet avertissement est supprimé dans Visual Studio 2017 version 15.5, car les commentaires à ligne unique sont standard C99.

Commentaires sur une ligne sont standard en C++ et C en commençant par C99 standard.
Sous compatibilité ANSI stricte ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), les fichiers C qui contiennent des commentaires à ligne unique, génèrent l’avertissement C4001 en raison de l’utilisation d’une extension non standard. Dans la mesure où les commentaires à ligne unique sont standard en C++, les fichiers C contenant des commentaires à ligne unique ne produisent pas C4001 lors de la compilation avec les extensions Microsoft (/Ze).

## <a name="example"></a>Exemple

Pour désactiver l’avertissement, supprimez les commentaires de [#pragma warning(disable:4001)](../../preprocessor/warning.md).

```
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```