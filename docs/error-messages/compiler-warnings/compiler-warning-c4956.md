---
description: 'En savoir plus sur : avertissement du compilateur C4956'
title: Avertissement du compilateur C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: 4a92c6329bf4cdd764fd7f419d8011d4dfde0202
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314839"
---
# <a name="compiler-warning-c4956"></a>Avertissement du compilateur C4956

> '*type*' : ce type n’est pas vérifiable

## <a name="remarks"></a>Notes

Cet avertissement est généré quand [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) est spécifié et que votre code contient un type qui n’est pas vérifiable. L’option de compilateur **/clr : safe** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Pour plus d’informations, consultez [Code pur et vérifiable (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Cet avertissement s’affiche comme une erreur et peut être désactivé avec le pragma [warning](../../preprocessor/warning.md) ou l’option du compilateur [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4956.

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```
