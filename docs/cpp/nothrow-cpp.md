---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 8164f47190267627bdaf7c7ee2f03f22f65c8f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161059"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Section spécifique de Microsoft**

**__Declspec** attribut étendu qui peut être utilisé dans la déclaration de fonctions.

## <a name="syntax"></a>Syntaxe

> *Return-type* __declspec (nothrow) [*Call-Convention*] *nom-fonction* ([*argument-List*])

## <a name="remarks"></a>Notes

Nous recommandons que tout nouveau code utilise l’opérateur [noexcept](noexcept-cpp.md) plutôt que `__declspec(nothrow)`.

Cet attribut indique au compilateur que la fonction déclarée et les fonctions qu'elle appelle ne lèvent jamais d'exception. Toutefois, elle n’applique pas la directive. En d’autres termes, il n’entraîne jamais l’appel de [std :: Terminate](../standard-library/exception-functions.md#terminate) , contrairement à `noexcept`, ou en mode **std : C++ 17** (Visual Studio 2017 version 15,5 et versions ultérieures), `throw()`.

Avec le modèle synchrone de gestion des exceptions, utilisé désormais par défaut, le compilateur peut éliminer les mécanismes de suivi de la durée de vie de certains objets non déroulables dans une telle fonction, et peut réduire considérablement la taille du code. À partir de la directive de préprocesseur suivante, les trois déclarations de fonction ci-dessous sont équivalentes dans **/std : mode c++ 14** :

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

En mode **/std : c++ 17** , `throw()` n’est pas équivalente aux autres qui utilisent `__declspec(nothrow)` parce qu’il entraîne l’appel de `std::terminate` si une exception est levée à partir de la fonction.

La déclaration `void __stdcall f3() throw();` utilise la syntaxe définie par la C++ norme. En C++ 17, le mot clé `throw()` était déconseillé.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
