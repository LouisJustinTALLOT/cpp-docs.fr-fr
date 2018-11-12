---
title: '/ Zc : noexcepttypes (règles c ++ 17 noexcept)'
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: f5f2fa3ef85e7ff15b28188e45a4ec397878873c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462229"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/ Zc : noexcepttypes (règles c ++ 17 noexcept)

La norme C ++ 17 rend `throw()` en tant qu’alias pour `noexcept`, supprime `throw(<type list>)` et `throw(...)`, ainsi que de certains types d’inclure `noexcept`. Cela peut entraîner un nombre de problèmes de compatibilité source dans le code qui est conforme à C ++ 14 ou une version antérieure. Le **/Zc : noexcepttypes** option peut spécifier la conformité à la norme C ++ 17 ou autoriser le C ++ 14 et versions antérieur comportement lorsque le code est compilé en mode C ++ 17.

## <a name="syntax"></a>Syntaxe

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>Notes

Lorsque le **/Zc : noexcepttypes** est spécifiée, le compilateur est conforme à la norme C ++ 17 et traite [throw()](../../cpp/exception-specifications-throw-cpp.md) en tant qu’alias pour [noexcept](../../cpp/noexcept-cpp.md), supprime `throw(<type list>)`et `throw(...)`, ainsi que de certains types d’inclure `noexcept`. Le **/Zc : noexcepttypes** option est disponible uniquement lorsque [/std : c ++ 17](std-specify-language-standard-version.md) ou [/std:latest](std-specify-language-standard-version.md) est activé. **/ Zc : noexcepttypes** est activée par défaut pour être conforme à la norme ISO C ++ 17 standard. Le [/ permissive-](permissive-standards-conformance.md) option n’affecte pas **/Zc : noexcepttypes**. Désactiver cette option en spécifiant **/Zc:noexceptTypes-** pour revenir à l’interface C ++ 14 de `noexcept` lorsque **/std::C ++ 17** ou **/std::latest** est spécifié.

À compter de Visual Studio 2017 version 15.5, le compilateur C++ diagnostique plusieurs spécifications d’exceptions incompatibles dans les déclarations en mode C ++ 17 ou lorsque le [/ permissive-](permissive-standards-conformance.md) option est spécifiée.

Cet exemple montre comment les déclarations avec un spécificateur d’exception comportent quand le **/Zc : noexcepttypes** option est définie ou désactivée. Pour afficher le comportement lorsque la valeur, compilez en utilisant `cl /EHsc /W4 noexceptTypes.cpp`. Pour afficher le comportement lorsque désactivée, compilez en utilisant `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Lors de la compilation en utilisant le paramètre par défaut **/Zc : noexcepttypes**, l’exemple génère les avertissements répertoriés. Pour mettre à jour votre code, utilisez à la place :

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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc : noexcepttypes** ou **/Zc:noexceptTypes-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md)
