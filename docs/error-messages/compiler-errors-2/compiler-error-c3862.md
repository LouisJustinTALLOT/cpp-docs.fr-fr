---
description: 'En savoir plus sur : erreur du compilateur C3862'
title: Erreur du compilateur C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: b8955a69bcd04c0a40aed8fab722c6c734bfa65b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222890"
---
# <a name="compiler-error-c3862"></a>Erreur du compilateur C3862

> '*fonction*' : impossible de compiler une fonction non managée avec/clr : pure ou/CLR : safe

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Une compilation avec **/clr : pure** ou **/clr : safe** produira une image MSIL uniquement, une image sans code natif (non managé).  Par conséquent, vous ne pouvez pas utiliser le `unmanaged` pragma dans une compilation **/clr : pure** ou **/clr : safe** .

Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) et [managé, non managé](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3862 :

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```
