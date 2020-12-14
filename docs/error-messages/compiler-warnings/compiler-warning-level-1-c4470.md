---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4470'
title: Avertissement du compilateur (niveau 1) C4470
ms.date: 11/04/2016
f1_keywords:
- C4470
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
ms.openlocfilehash: 6fe01782fbd2151175bc1da59afa8bd73fa5648d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310978"
---
# <a name="compiler-warning-level-1-c4470"></a>Avertissement du compilateur (niveau 1) C4470

pragmas de contrôle à virgule flottante ignorés sous/CLR

Pragmas de contrôle float :

- [fenv_access](../../preprocessor/fenv-access.md)

- [float_control](../../preprocessor/float-control.md)

- [fp_contract](../../preprocessor/fp-contract.md)

n’ont aucun effet sous [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

L’exemple suivant génère l’C4470 :

```cpp
// C4470.cpp
// compile with: /clr /W1 /LD
#pragma float_control(except, on)   // C4470
```
