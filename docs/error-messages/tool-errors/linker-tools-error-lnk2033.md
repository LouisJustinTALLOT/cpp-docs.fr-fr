---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2033'
title: Erreur des outils Éditeur de liens LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 46ee94e0aff4379a6d28a508ed1394e90ef9a96d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275644"
---
# <a name="linker-tools-error-lnk2033"></a>Erreur des outils Éditeur de liens LNK2033

jeton TypeRef non résolu (jeton) pour’type'

Un type n’a pas de définition dans les métadonnées MSIL.

LNK2033 peut se produire lors de la compilation avec **/clr : safe** et lorsqu’il n’existe qu’une déclaration anticipée pour un type dans un module MSIL, où le type est référencé dans le module MSIL.

Le type doit être défini sous **/clr : safe**.

Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK2033.

```cpp
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
