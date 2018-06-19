---
title: '-Zc : noexceptTypes (C ++ 17 noexcept règles) | Documents Microsoft'
ms.date: 11/14/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:noexceptTypes
dev_langs:
- C++
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25ad2a662af2cda49e3e8dd8c769fa75dafee94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379547"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (c ++ 17 noexcept règles)

La norme C ++ 17 rend `throw()` en tant qu’alias pour `noexcept`, supprime `throw(<type list>)` et `throw(...)`et permet d’inclure certains types de `noexcept`. Cela peut provoquer un numéro de la source des problèmes de compatibilité dans du code conforme à C ++ 14 ou une version antérieure. Le **/Zc:noexceptTypes** option peut spécifier la conformité à la norme C ++ 17 ou autoriser le C ++ 14 et versions antérieur du comportement lorsque le code est compilé en mode C ++ 17.

## <a name="syntax"></a>Syntaxe

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>Notes

Lorsque le **/Zc:noexceptTypes** est spécifiée, le compilateur est conforme à la norme C ++ 17 et traite [throw()](../../cpp/exception-specifications-throw-cpp.md) en tant qu’alias pour [noexcept](../../cpp/noexcept-cpp.md), supprime `throw(<type list>)`et `throw(...)`et permet d’inclure certains types de `noexcept`. Le **/Zc:noexceptTypes** option est disponible uniquement lorsque [/std : c ++ 17](std-specify-language-standard-version.md) ou [/std:latest](std-specify-language-standard-version.md) est activé. **/Zc:noexceptTypes** est activée par défaut pour se conformer à la norme ISO C ++ 17 standard. Le [/ permissive-](permissive-standards-conformance.md) option n’affecte pas **/Zc:noexceptTypes**. Désactiver cette option en spécifiant **/Zc:noexceptTypes-** pour rétablir le comportement 14 C ++ de `noexcept` lorsque **/std::C ++ 17** ou **/std::latest** est spécifié.

À compter de Visual Studio 2017 version 15.5, le compilateur C++ permet de diagnostiquer plusieurs spécifications d’exception ne correspondent pas dans les déclarations de mode C ++ 17 ou lorsque le [/ permissive-](permissive-standards-conformance.md) option est spécifiée.

Cet exemple montre comment les déclarations avec un spécificateur d’exception comportent quand le **/Zc:noexceptTypes** option est définie ou désactivée. Pour afficher le comportement lorsque vous définissez, compilez en utilisant `cl /EHsc /W4 noexceptTypes.cpp`. Pour afficher le comportement lorsque désactivée, compilez en utilisant `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Lors de la compilation à l’aide du paramètre par défaut **/Zc:noexceptTypes**, l’exemple génère les avertissements répertoriés. Pour mettre à jour votre code, utilisez à la place :

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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier la **des Options supplémentaires** propriété à inclure **/Zc:noexceptTypes** ou **/Zc:noexceptTypes-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)  
[noexcept](../../cpp/noexcept-cpp.md)  
[Spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md)  
