---
title: Erreur LNK2033 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2033
dev_langs:
- C++
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6c547b4d35e2e7fe057cdd67f0dad47f58d000c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039989"
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