---
title: Erreur des outils Éditeur de liens LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 7e95823e23215848ff3e5d201171523c9009eb2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571884"
---
# <a name="linker-tools-error-lnk2033"></a>Erreur des outils Éditeur de liens LNK2033

jeton typeref non résolu (jeton) pour 'type'

Un type ne possède pas une définition dans les métadonnées MSIL.

LNK2033 peut se produire lors de la compilation avec **/CLR : safe** et où il est uniquement une déclaration anticipée pour un type dans un module MSIL, où le type est référencé dans le module MSIL.

Le type doit être défini sous **/CLR : safe**.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK2033.

```
// LNK2033.cpp
// compile with: /clr:safe
// LNK2033 expected
ref class A;
ref class B {};

int main() {
   A ^ aa = nullptr;
   B ^ bb = nullptr;   // OK
};
```