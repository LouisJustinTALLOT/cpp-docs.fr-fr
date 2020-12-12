---
description: 'En savoir plus sur : erreur du compilateur C3872'
title: Erreur du compilateur C3872
ms.date: 11/04/2016
f1_keywords:
- C3872
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
ms.openlocfilehash: 860db2f94fa198246290a0e491b1a647dbc91c20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222734"
---
# <a name="compiler-error-c3872"></a>Erreur du compilateur C3872

’char’ : ce caractère n’est pas autorisé dans un identificateur

Le compilateur C++ suit la norme C++11 sur les caractères autorisés dans un identificateur. Seules certaines plages de caractères et certains noms de caractères universels sont autorisés dans un identificateur. Des restrictions supplémentaires s’appliquent au premier caractère d’un identificateur. Pour plus d’informations et une liste des caractères et des plages de noms de caractère universel autorisés, consultez [Identifiers](../../cpp/identifiers-cpp.md).

La plage des caractères autorisés dans un identificateur est moins restrictive durant la compilation du code C++/CLI. Les identificateurs contenus dans du code compilé à l’aide de /clr doivent suivre la  [norme ECMA-335 : Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

L’exemple suivant génère l’erreur C3872 :

```cpp
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```
