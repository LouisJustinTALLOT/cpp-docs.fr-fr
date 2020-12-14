---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4297'
title: Avertissement du compilateur (niveau 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: ef330302702ee9e7a8fa55128a6f1f61732552f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311732"
---
# <a name="compiler-warning-level-1-c4297"></a>Avertissement du compilateur (niveau 1) C4297

'fonction' : la fonction lève une exception alors qu'elle est présumée ne pas le faire

Une déclaration de fonction contient un spécificateur (éventuellement implicite) **`noexcept`** , un **`throw`** spécificateur d’exception vide ou un attribut [__declspec (nothrow)](../../cpp/nothrow-cpp.md) , et la définition contient une ou plusieurs instructions [throw](../../cpp/try-throw-and-catch-statements-cpp.md) . Pour résoudre l'avertissement C4297, ne tentez pas de lever des exceptions dans les fonctions qui sont déclarées `__declspec(nothrow)`, `noexcept(true)` ou `throw()`. Vous pouvez également supprimer la **`noexcept`** `throw()` spécification, ou `__declspec(nothrow)` .

Par défaut, le compilateur génère des spécificateurs `noexcept(true)` implicites pour les fonctions annulatrices d'allocation et les destructeurs définis par l'utilisateur, ainsi que pour les fonctions membres spéciales générées par le compilateur. Cela est conforme à la norme ISO C++11. Pour empêcher la génération de spécificateurs noexcept implicites et rétablir le compilateur sur le comportement non standard de Visual Studio 2013, utilisez l’option de compilateur **/Zc : implicitNoexcept-** . Pour plus d’informations, consultez [/Zc : implicitNoexcept (spécificateurs d’exceptions implicites)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Pour plus d’informations sur les spécifications d’exceptions, consultez [spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md). Pour plus d’informations sur la modification du comportement de gestion des exceptions au moment de la compilation, consultez l’article [/Eh (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md) .

Cet avertissement est également généré pour les fonctions __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) marquées extern "C", même s’il s’agit de fonctions C++.

L'exemple suivant génère l'avertissement C4297 :

```cpp
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```
