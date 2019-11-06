---
title: /Zc:noexceptTypes (Règles noexcept C++17)
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 35bea7c2c629c615c60a6136f289b6b11926c054
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624866"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (Règles noexcept C++17)

La norme C++ 17 crée `throw()` alias pour `noexcept`, supprime `throw(<type list>)` et `throw(...)`, et autorise certains types à inclure des `noexcept`. Cette modification peut entraîner un certain nombre de problèmes de compatibilité source dans le code qui est conforme à C++ 14 ou version antérieure. L’option **/Zc : noexceptTypes** spécifie la conformité à la norme c++ 17. **/Zc : noexceptTypes-** autorise le comportement c++ 14 et antérieur lorsque le code est compilé en mode c++ 17.

## <a name="syntax"></a>Syntaxe

> **/Zc : noexceptTypes**[-]

## <a name="remarks"></a>Notes

Lorsque l’option **/Zc : noexceptTypes** est spécifiée, le compilateur est conforme à la norme c++ 17 et traite [Throw ()](../../cpp/exception-specifications-throw-cpp.md) comme alias pour [noexcept](../../cpp/noexcept-cpp.md), supprime `throw(<type list>)` et `throw(...)`, et autorise certains types à inclure des `noexcept`. L’option **/Zc : noexceptTypes** est disponible uniquement lorsque [/std : c++ 17](std-specify-language-standard-version.md) ou [/std : latest](std-specify-language-standard-version.md) est activé. **/Zc : noexceptTypes** est activé par défaut pour se conformer à la norme ISO c++ 17. L’option [/permissive-](permissive-standards-conformance.md) n’a pas d’incidence sur **/Zc : noexceptTypes**. Désactivez cette option en spécifiant **/Zc : noexceptTypes-** pour rétablir le comportement c++ 14 de `noexcept` lorsque **/std : c++ 17** ou **/std : latest** est spécifié.

À compter de Visual Studio 2017 version 15,5, C++ le compilateur diagnostique les spécifications d’exceptions plus incompatibles dans les déclarations en mode c++ 17 ou lorsque vous spécifiez l’option [/permissive-](permissive-standards-conformance.md) .

Cet exemple montre comment les déclarations avec un spécificateur d’exception se comportent quand l’option **/Zc : noexceptTypes** est définie ou désactivée. Pour afficher le comportement lorsqu’il est défini, compilez à l’aide de `cl /EHsc /W4 noexceptTypes.cpp`. Pour afficher le comportement quand il est désactivé, compilez à l’aide de `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

En cas de compilation à l’aide du paramètre par défaut **/Zc : noexceptTypes**, l’exemple génère les avertissements listés. Pour mettre à jour votre code, utilisez la commande suivante à la place :

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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour obtenir des informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++**  > **Ligne de commande**.

1. Modifiez la propriété **options supplémentaires** pour inclure **/Zc : noexceptTypes** ou **/Zc : NoexceptTypes-** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

\ [/Zc (conformité)](zc-conformance.md)
[noexcept](../../cpp/noexcept-cpp.md)\
[Spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md)
