---
title: Avertissement du compilateur (niveau 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 07dd6c65498ddd0d377ec3e0fbc7b44e52bec96b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408626"
---
# <a name="compiler-warning-level-1-c4297"></a>Avertissement du compilateur (niveau 1) C4297

'fonction' : la fonction lève une exception alors qu'elle est présumée ne pas le faire

Une déclaration de fonction contient un (l’éventuellement implicite) `noexcept` spécificateur, vide `throw` spécificateur d’exception, ou un [__declspec (nothrow)](../../cpp/nothrow-cpp.md) attribut et la définition contient un ou plusieurs [lever ](../../cpp/try-throw-and-catch-statements-cpp.md) instructions. Pour résoudre l'avertissement C4297, ne tentez pas de lever des exceptions dans les fonctions qui sont déclarées `__declspec(nothrow)`, `noexcept(true)` ou `throw()`. Vous pouvez également supprimer la spécification `noexcept`, `throw()` ou `__declspec(nothrow)`.

Par défaut, le compilateur génère des spécificateurs `noexcept(true)` implicites pour les fonctions annulatrices d'allocation et les destructeurs définis par l'utilisateur, ainsi que pour les fonctions membres spéciales générées par le compilateur. Cela est conforme à la norme ISO C++11. Pour empêcher la génération des spécificateurs noexcept implicites et rétablir le comportement non standard de Visual Studio 2013, utilisez le **/Zc:implicitNoexcept-** option du compilateur. Pour plus d’informations, consultez [/Zc : implicitnoexcept (spécificateurs d’exceptions implicites)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Pour plus d’informations sur les spécifications d’exceptions, consultez [spécifications d’Exception (throw)](../../cpp/exception-specifications-throw-cpp.md). En outre, consultez [/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md) pour plus d’informations sur la façon de modifier le comportement des exceptions au moment de la compilation.

Cet avertissement est également généré pour __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) les fonctions marquées extern « C », même s’ils sont C++ fonctions.

L'exemple suivant génère l'avertissement C4297 :

```
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```