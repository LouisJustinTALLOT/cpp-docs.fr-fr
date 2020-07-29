---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 8ce0e9ea6a39ef7760c7a6d0802913326433cf68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227268"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Spécifique à Microsoft**

**`__declspec`** Attribut étendu qui peut être utilisé dans la déclaration de fonctions.

## <a name="syntax"></a>Syntaxe

> *Return-type* __declspec (nothrow) [*Call-Convention*] *nom-fonction* ([*argument-List*])

## <a name="remarks"></a>Notes

Nous recommandons que tout nouveau code utilise l’opérateur [noexcept](noexcept-cpp.md) plutôt que `__declspec(nothrow)` .

Cet attribut indique au compilateur que la fonction déclarée et les fonctions qu'elle appelle ne lèvent jamais d'exception. Toutefois, elle n’applique pas la directive. En d’autres termes, il n’entraîne jamais l’appel de [std :: Terminate](../standard-library/exception-functions.md#terminate) , contrairement à **`noexcept`** ou en mode **std : C++ 17** (Visual Studio 2017 version 15,5 et versions ultérieures), `throw()` .

Avec le modèle synchrone de gestion des exceptions, utilisé désormais par défaut, le compilateur peut éliminer les mécanismes de suivi de la durée de vie de certains objets non déroulables dans une telle fonction, et peut réduire considérablement la taille du code. À partir de la directive de préprocesseur suivante, les trois déclarations de fonction ci-dessous sont équivalentes dans **/std : mode c++ 14** :

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

En mode **/std : c++ 17** , `throw()` n’est pas équivalent aux autres qui utilisent `__declspec(nothrow)` parce qu’il entraîne `std::terminate` l’appel de si une exception est levée à partir de la fonction.

La `void __stdcall f3() throw();` déclaration utilise la syntaxe définie par la norme C++. Dans C++ 17, le `throw()` mot clé était déconseillé.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
