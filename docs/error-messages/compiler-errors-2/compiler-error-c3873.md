---
title: Erreur du compilateur C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: eb2a6935073c3b4a2b9eb3d9b099b372cfa34303
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467355"
---
# <a name="compiler-error-c3873"></a>Erreur du compilateur C3873

« char » : ce caractère n’est pas autorisé comme premier caractère d’identifiant

Le compilateur C++ suit la norme C++11 sur les caractères autorisés dans un identificateur. Seules certaines plages de caractères et certains noms de caractères universels sont autorisés dans un identificateur. Des restrictions supplémentaires s’appliquent au premier caractère d’un identificateur. Pour plus d’informations et une liste des caractères et des plages de noms de caractère universel autorisés, consultez [Identifiers](../../cpp/identifiers-cpp.md).

La plage de caractères autorisés dans un identificateur est moins restrictive lors de la compilation de code C++/CLI. Les identificateurs dans du code compilé en utilisant /clr doivent suivre  la  [Norme ECMA-335 : Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).

L’exemple suivant génère l’erreur C3873 :

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```