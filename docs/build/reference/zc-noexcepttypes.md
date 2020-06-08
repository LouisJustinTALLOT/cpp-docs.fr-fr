---
title: /Zc:noexceptTypes (Règles noexcept C++17)
ms.date: 06/04/2020
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 0f833209938ccc09cbc37235788b6f719d4d12d4
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84506869"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (Règles noexcept C++17)

La norme c++ 17 crée `throw()` un alias pour `noexcept` , supprime `throw(` *`type-list`* `)` et `throw(...)` , et autorise l’inclusion de certains types `noexcept` . Cette modification peut entraîner un certain nombre de problèmes de compatibilité source dans le code qui est conforme à C++ 14 ou version antérieure. L' **`/Zc:noexceptTypes`** option spécifie la conformité à la norme c++ 17. **`/Zc:noexceptTypes-`** autorise le comportement C++ 14 et antérieur lorsque le code est compilé en mode C++ 17.

## <a name="syntax"></a>Syntaxe

> **`/Zc:noexceptTypes`**\[**`-`**]

## <a name="remarks"></a>Remarques

Lorsque l' **`/Zc:noexceptTypes`** option est spécifiée, le compilateur est conforme à la norme c++ 17 et traite [**`throw()`**](../../cpp/exception-specifications-throw-cpp.md) comme un alias pour [**`noexcept`**](../../cpp/noexcept-cpp.md) , supprime `throw(` *`type-list`* `)` et et `throw(...)` autorise certains types à inclure **`noexcept`** . L' **`/Zc:noexceptTypes`** option est disponible uniquement lorsque [**`/std:c++17`**](std-specify-language-standard-version.md) ou [**`/std:c++latest`**](std-specify-language-standard-version.md) est activé. **`/Zc:noexceptTypes`** est activé par défaut pour se conformer à la norme ISO C++ 17. L' [**`/permissive-`**](permissive-standards-conformance.md) option n’a aucune incidence sur **`/Zc:noexceptTypes`** . Désactivez cette option en spécifiant **`/Zc:noexceptTypes-`** pour revenir au comportement c++ 14 de **`noexcept`** quand **`/std:c++17`** ou **`/std:c++latest`** est spécifié.

À compter de Visual Studio 2017 version 15,5, le compilateur C++ diagnostique les spécifications d’exceptions plus incompatibles dans les déclarations en mode C++ 17, ou lorsque vous spécifiez l' [**`/permissive-`**](permissive-standards-conformance.md) option.

Cet exemple montre comment les déclarations avec un spécificateur d’exception se comportent lorsque l' **`/Zc:noexceptTypes`** option est définie ou désactivée. Pour afficher le comportement lorsqu’il est défini, compilez à l’aide de `cl /EHsc /W4 noexceptTypes.cpp` . Pour afficher le comportement quand il est désactivé, compilez à l’aide de `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp` .

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

Lorsqu’il est compilé à l’aide du paramètre par défaut **`/Zc:noexceptTypes`** , l’exemple génère les avertissements listés. Pour mettre à jour votre code, utilisez la commande suivante à la place :

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour inclure *`/Zc:noexceptTypes`* ou *`/Zc:noexceptTypes-`* , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[**`/Zc`** Conformité](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[Spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md)
