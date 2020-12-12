---
description: 'En savoir plus sur : erreur du compilateur C2393'
title: Erreur du compilateur C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: 7cf1b333afac9f976bb4bf38ce769e6982255959
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318986"
---
# <a name="compiler-error-c2393"></a>Erreur du compilateur C2393

> '*symbol*' : un symbole par AppDomain ne peut pas être alloué dans le segment'*segment*'

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

L’utilisation de variables [AppDomain](../../cpp/appdomain.md) implique la compilation avec **/clr : pure** ou **/clr : safe**, et une image safe ou pure ne peut pas contenir de segments de données.

Pour plus d’informations [, consultez/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2393. Pour résoudre ce problème, ne créez pas de segment de données.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```
