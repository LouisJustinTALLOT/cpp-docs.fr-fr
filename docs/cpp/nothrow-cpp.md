---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 88041b374cc48ac31c8990aa7f867ba25b33e1d7
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345882"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Section spécifique à Microsoft**

Un **__declspec** des attributs étendus, qui peuvent être utilisé dans la déclaration de fonctions.

## <a name="syntax"></a>Syntaxe

> *return-type* __declspec(nothrow) [*call-convention*] *function-name* ([*argument-list*])

## <a name="remarks"></a>Notes

Nous recommandons d’utiliser tout nouveau code de la [noexcept](noexcept-cpp.md) opérateur plutôt que `__declspec(nothrow)`.

Cet attribut indique au compilateur que la fonction déclarée et les fonctions qu'elle appelle ne lèvent jamais d'exception. Toutefois, il n’applique pas la directive. En d’autres termes, elle ne génère jamais [std::terminate](../standard-library/exception-functions.md#terminate) à appeler, contrairement à `noexcept`, ou dans **std : c ++ 17** (Visual Studio 2017 version 15.5 et versions ultérieure), le mode `throw()`.

Avec le modèle synchrone de gestion des exceptions, utilisé désormais par défaut, le compilateur peut éliminer les mécanismes de suivi de la durée de vie de certains objets non déroulables dans une telle fonction, et peut réduire considérablement la taille du code. Étant donné la directive de préprocesseur suivante, les trois déclarations de fonction ci-dessous sont équivalentes dans **/std : c ++ 14** mode :

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

Dans **/std : c ++ 17** mode, `throw()` n’est pas équivalent à ceux qui utilisent `__declspec(nothrow)` , car elle force `std::terminate` d’être appelée si une exception est levée à partir de la fonction.

Le `void __stdcall f3() throw();` déclaration utilise la syntaxe définie par la norme C++. Dans C ++ 17 le `throw()` mot clé a été déconseillé.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)