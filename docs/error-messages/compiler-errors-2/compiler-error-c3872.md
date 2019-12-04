---
title: Erreur du compilateur C3872
ms.date: 11/04/2016
f1_keywords:
- C3872
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
ms.openlocfilehash: f4b116729ad3b84014d202deb31ab490435fcef3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761440"
---
# <a name="compiler-error-c3872"></a>Erreur du compilateur C3872

’char’ : ce caractère n’est pas autorisé dans un identificateur

Le compilateur C++ suit la norme C++11 sur les caractères autorisés dans un identificateur. Seules certaines plages de caractères et certains noms de caractères universels sont autorisés dans un identificateur. Des restrictions supplémentaires s’appliquent au premier caractère d’un identificateur. Pour plus d’informations et une liste des caractères et des plages de noms de caractère universel autorisés, consultez [Identifiers](../../cpp/identifiers-cpp.md).

La plage de caractères autorisés dans un identificateur est moins restrictive lors de la compilation de code C++/CLI. Les identificateurs dans du code compilé en utilisant /clr doivent suivre  la  [Norme ECMA-335 : Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

L’exemple suivant génère l’erreur C3872 :

```cpp
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```
