---
description: 'En savoir plus sur : erreur du compilateur C3873'
title: Erreur du compilateur C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: 7ca1346d2a1f22e1aa8bd2a7197daa41d8b416aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222721"
---
# <a name="compiler-error-c3873"></a>Erreur du compilateur C3873

« char » : ce caractère n’est pas autorisé comme premier caractère d’identifiant

Le compilateur C++ suit la norme C++11 sur les caractères autorisés dans un identificateur. Seules certaines plages de caractères et certains noms de caractères universels sont autorisés dans un identificateur. Des restrictions supplémentaires s’appliquent au premier caractère d’un identificateur. Pour plus d’informations et une liste des caractères et des plages de noms de caractère universel autorisés, consultez [Identifiers](../../cpp/identifiers-cpp.md).

La plage des caractères autorisés dans un identificateur est moins restrictive durant la compilation du code C++/CLI. Les identificateurs contenus dans du code compilé à l’aide de /clr doivent suivre la  [norme ECMA-335 : Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

L’exemple suivant génère l’erreur C3873 :

```cpp
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```
