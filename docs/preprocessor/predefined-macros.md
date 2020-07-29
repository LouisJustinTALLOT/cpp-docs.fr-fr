---
title: Macros prédéfinies
description: Répertorie et décrit les macros de préprocesseur prédéfinies du compilateur Microsoft C++.
ms.custom: update_every_version
ms.date: 06/08/2020
f1_keywords:
- ':::no-loc(_ATL_VER):::'
- ':::no-loc(__ATOM__):::'
- ':::no-loc(__AVX__):::'
- ':::no-loc(__AVX2__):::'
- ':::no-loc(__AVX512BW__):::'
- ':::no-loc(__AVX512CD__):::'
- ':::no-loc(__AVX512DQ__):::'
- ':::no-loc(__AVX512F__):::'
- ':::no-loc(__AVX512VL__):::'
- ':::no-loc(_CHAR_UNSIGNED):::'
- ':::no-loc(__CLR_VER):::'
- ':::no-loc(_CONTROL_FLOW_GUARD):::'
- ':::no-loc(__COUNTER__):::'
- ':::no-loc(__cplusplus):::'
- ':::no-loc(__cplusplus_cli):::'
- ':::no-loc(__cplusplus_winrt):::'
- ':::no-loc(_CPPRTTI):::'
- ':::no-loc(_CPPUNWIND):::'
- ':::no-loc(__DATE__):::'
- ':::no-loc(_DEBUG):::'
- ':::no-loc(_DLL):::'
- ':::no-loc(__FILE__):::'
- ':::no-loc(__FUNCDNAME__):::'
- ':::no-loc(__FUNCSIG__):::'
- ':::no-loc(__FUNCTION__):::'
- ':::no-loc(_INTEGRAL_MAX_BITS):::'
- ':::no-loc(_ISO_VOLATILE):::'
- ':::no-loc(_KERNEL_MODE):::'
- ':::no-loc(__LINE__):::'
- ':::no-loc(_M_AMD64):::'
- ':::no-loc(_M_ARM):::'
- ':::no-loc(_M_ARM_ARMV7VE):::'
- ':::no-loc(_M_ARM_FP):::'
- ':::no-loc(_M_ARM64):::'
- ':::no-loc(_M_CEE):::'
- ':::no-loc(_M_CEE_PURE):::'
- ':::no-loc(_M_CEE_SAFE):::'
- ':::no-loc(_M_FP_EXCEPT):::'
- ':::no-loc(_M_FP_FAST):::'
- ':::no-loc(_M_FP_PRECISE):::'
- ':::no-loc(_M_FP_STRICT):::'
- ':::no-loc(_M_IX86):::'
- ':::no-loc(_M_IX86_FP):::'
- ':::no-loc(_M_X64):::'
- ':::no-loc(_MANAGED):::'
- ':::no-loc(_MFC_VER):::'
- ':::no-loc(_MSC_BUILD):::'
- ':::no-loc(_MSC_EXTENSIONS):::'
- ':::no-loc(_MSC_FULL_VER):::'
- ':::no-loc(_MSC_VER):::'
- ':::no-loc(_MSVC_LANG):::'
- ':::no-loc(__MSVC_RUNTIME_CHECKS):::'
- ':::no-loc(_MT):::'
- ':::no-loc(_NATIVE_WCHAR_T_DEFINED):::'
- ':::no-loc(_NO_SIZED_DEALLOCATION):::'
- ':::no-loc(_OPENMP):::'
- ':::no-loc(_PREFAST_):::'
- ':::no-loc(_RESUMABLE_FUNCTIONS_SUPPORTED):::'
- ':::no-loc(_RTC_CONVERSION_CHECKS_ENABLED):::'
- ':::no-loc(__STDC__):::'
- ':::no-loc(__STDC_HOSTED__):::'
- ':::no-loc(__STDCPP_THREADS__):::'
- ':::no-loc(__TIME__):::'
- ':::no-loc(__TIMESTAMP__):::'
- ':::no-loc(__VA_ARGS__):::'
- ':::no-loc(_VC_NODEFAULTLIB):::'
- ':::no-loc(_WCHAR_T_DEFINED):::'
- ':::no-loc(_WIN32):::'
- ':::no-loc(_WIN64):::'
- ':::no-loc(_WINRT_DLL):::'
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- ':::no-loc(_ATL_VER)::: macro'
- ':::no-loc(__ATOM__)::: macro'
- ':::no-loc(__AVX__)::: macro'
- ':::no-loc(__AVX2__)::: macro'
- ':::no-loc(__AVX512BW__)::: macro'
- ':::no-loc(__AVX512CD__)::: macro'
- ':::no-loc(__AVX512DQ__)::: macro'
- ':::no-loc(__AVX512F__)::: macro'
- ':::no-loc(__AVX512VL__)::: macro'
- ':::no-loc(_CHAR_UNSIGNED)::: macro'
- ':::no-loc(__CLR_VER)::: macro'
- ':::no-loc(_CONTROL_FLOW_GUARD)::: macro'
- ':::no-loc(__COUNTER__)::: macro'
- ':::no-loc(__cplusplus)::: macro'
- ':::no-loc(__cplusplus_cli)::: macro'
- ':::no-loc(__cplusplus_winrt)::: macro'
- ':::no-loc(_CPPRTTI)::: macro'
- ':::no-loc(_CPPUNWIND)::: macro'
- ':::no-loc(__DATE__)::: macro'
- ':::no-loc(_DEBUG)::: macro'
- ':::no-loc(_DLL)::: macro'
- ':::no-loc(__FILE__)::: macro'
- ':::no-loc(__FUNCDNAME__)::: macro'
- ':::no-loc(__FUNCSIG__)::: macro'
- ':::no-loc(__FUNCTION__)::: macro'
- ':::no-loc(_INTEGRAL_MAX_BITS)::: macro'
- ':::no-loc(_ISO_VOLATILE)::: macro'
- ':::no-loc(_KERNEL_MODE)::: macro'
- ':::no-loc(__LINE__)::: macro'
- ':::no-loc(_M_AMD64)::: macro'
- ':::no-loc(_M_ARM)::: macro'
- ':::no-loc(_M_ARM_ARMV7VE)::: macro'
- ':::no-loc(_M_ARM_FP)::: macro'
- ':::no-loc(_M_ARM64)::: macro'
- ':::no-loc(_M_CEE)::: macro'
- ':::no-loc(_M_CEE_PURE)::: macro'
- ':::no-loc(_M_CEE_SAFE)::: macro'
- ':::no-loc(_M_FP_EXCEPT)::: macro'
- ':::no-loc(_M_FP_FAST)::: macro'
- ':::no-loc(_M_FP_PRECISE)::: macro'
- ':::no-loc(_M_FP_STRICT)::: macro'
- ':::no-loc(_M_IX86)::: macro'
- ':::no-loc(_M_IX86_FP)::: macro'
- ':::no-loc(_M_X64)::: macro'
- ':::no-loc(_MANAGED)::: macro'
- ':::no-loc(_MFC_VER)::: macro'
- ':::no-loc(_MSC_BUILD)::: macro'
- ':::no-loc(_MSC_EXTENSIONS)::: macro'
- ':::no-loc(_MSC_FULL_VER)::: macro'
- ':::no-loc(_MSC_VER)::: macro'
- ':::no-loc(_MSVC_LANG)::: macro'
- ':::no-loc(__MSVC_RUNTIME_CHECKS)::: macro'
- ':::no-loc(_MT)::: macro'
- ':::no-loc(_NATIVE_WCHAR_T_DEFINED)::: macro'
- ':::no-loc(_NO_SIZED_DEALLOCATION)::: macro'
- ':::no-loc(_OPENMP)::: macro'
- ':::no-loc(_PREFAST_)::: macro'
- ':::no-loc(_RESUMABLE_FUNCTIONS_SUPPORTED)::: macro'
- ':::no-loc(_RTC_CONVERSION_CHECKS_ENABLED)::: macro'
- ':::no-loc(__STDC__)::: macro'
- ':::no-loc(__STDC_HOSTED__)::: macro'
- ':::no-loc(__STDCPP_THREADS__)::: macro'
- ':::no-loc(__TIME__)::: macro'
- ':::no-loc(__TIMESTAMP__)::: macro'
- ':::no-loc(__VA_ARGS__)::: macro'
- ':::no-loc(_VC_NODEFAULTLIB)::: macro'
- ':::no-loc(_WCHAR_T_DEFINED)::: macro'
- ':::no-loc(_WIN32)::: macro'
- ':::no-loc(_WIN64)::: macro'
- ':::no-loc(_WINRT_DLL)::: macro'
- ':::no-loc(__func__)::: identifier'
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
no-loc:
- ':::no-loc(_ATL_VER):::'
- ':::no-loc(__ATOM__):::'
- ':::no-loc(__AVX__):::'
- ':::no-loc(__AVX2__):::'
- ':::no-loc(__AVX512BW__):::'
- ':::no-loc(__AVX512CD__):::'
- ':::no-loc(__AVX512DQ__):::'
- ':::no-loc(__AVX512F__):::'
- ':::no-loc(__AVX512VL__):::'
- ':::no-loc(_CHAR_UNSIGNED):::'
- ':::no-loc(__CLR_VER):::'
- ':::no-loc(_CONTROL_FLOW_GUARD):::'
- ':::no-loc(__COUNTER__):::'
- ':::no-loc(__cplusplus):::'
- ':::no-loc(__cplusplus_cli):::'
- ':::no-loc(__cplusplus_winrt):::'
- ':::no-loc(_CPPRTTI):::'
- ':::no-loc(_CPPUNWIND):::'
- ':::no-loc(__DATE__):::'
- ':::no-loc(_DEBUG):::'
- ':::no-loc(_DLL):::'
- ':::no-loc(__FILE__):::'
- ':::no-loc(__FUNCDNAME__):::'
- ':::no-loc(__FUNCSIG__):::'
- ':::no-loc(__FUNCTION__):::'
- ':::no-loc(_INTEGRAL_MAX_BITS):::'
- ':::no-loc(_ISO_VOLATILE):::'
- ':::no-loc(_KERNEL_MODE):::'
- ':::no-loc(__LINE__):::'
- ':::no-loc(_M_AMD64):::'
- ':::no-loc(_M_ARM):::'
- ':::no-loc(_M_ARM_ARMV7VE):::'
- ':::no-loc(_M_ARM_FP):::'
- ':::no-loc(_M_ARM64):::'
- ':::no-loc(_M_CEE):::'
- ':::no-loc(_M_CEE_PURE):::'
- ':::no-loc(_M_CEE_SAFE):::'
- ':::no-loc(_M_FP_EXCEPT):::'
- ':::no-loc(_M_FP_FAST):::'
- ':::no-loc(_M_FP_PRECISE):::'
- ':::no-loc(_M_FP_STRICT):::'
- ':::no-loc(_M_IX86):::'
- ':::no-loc(_M_IX86_FP):::'
- ':::no-loc(_M_X64):::'
- ':::no-loc(_MANAGED):::'
- ':::no-loc(_MFC_VER):::'
- ':::no-loc(_MSC_BUILD):::'
- ':::no-loc(_MSC_EXTENSIONS):::'
- ':::no-loc(_MSC_FULL_VER):::'
- ':::no-loc(_MSC_VER):::'
- ':::no-loc(_MSVC_LANG):::'
- ':::no-loc(__MSVC_RUNTIME_CHECKS):::'
- ':::no-loc(_MT):::'
- ':::no-loc(_NATIVE_WCHAR_T_DEFINED):::'
- ':::no-loc(_NO_SIZED_DEALLOCATION):::'
- ':::no-loc(_OPENMP):::'
- ':::no-loc(_PREFAST_):::'
- ':::no-loc(_RESUMABLE_FUNCTIONS_SUPPORTED):::'
- ':::no-loc(_RTC_CONVERSION_CHECKS_ENABLED):::'
- ':::no-loc(__STDC__):::'
- ':::no-loc(__STDC_HOSTED__):::'
- ':::no-loc(__STDCPP_THREADS__):::'
- ':::no-loc(__TIME__):::'
- ':::no-loc(__TIMESTAMP__):::'
- ':::no-loc(__VA_ARGS__):::'
- ':::no-loc(_VC_NODEFAULTLIB):::'
- ':::no-loc(_WCHAR_T_DEFINED):::'
- ':::no-loc(_WIN32):::'
- ':::no-loc(_WIN64):::'
- ':::no-loc(_WINRT_DLL):::'
- ':::no-loc(__func__):::'
ms.openlocfilehash: 1c7b2f18aede84d8067c36537f33261554c16c17
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222639"
---
# <a name="predefined-macros"></a>Macros prédéfinies

Le compilateur Microsoft C/C++ (MSVC) prédéfinit certaines macros de préprocesseur, en fonction du langage (C ou C++), de la cible de compilation et des options de compilateur choisies.

MSVC prend en charge les macros de préprocesseur prédéfinies requises par les normes ANSI/ISO C99 standard et ISO C++ 14 et C++ 17. L’implémentation prend également en charge plusieurs macros de préprocesseur spécifiques à Microsoft. Certaines macros sont définies uniquement pour des environnements de génération ou des options de compilateur spécifiques. Sauf mention contraire, les macros sont définies dans toute l’unité de traduction comme si elles étaient spécifiées en tant qu’arguments de l' **`/D`** option du compilateur. Lorsqu’elles sont définies, les macros sont développées aux valeurs spécifiées par le préprocesseur avant la compilation. Les macros prédéfinies ne prennent pas d’arguments et ne peuvent pas être redéfinies.

## <a name="standard-predefined-identifier"></a>Identificateur prédéfini standard

Le compilateur prend en charge cet identificateur prédéfini spécifié par ISO C99 et ISO C++ 11.

- `:::no-loc(__func__):::`Nom non qualifié et sans ornement de la fonction englobante en tant que tableau **statique statique** de fonction local de **`char`** .

    ```cpp
    void example(){
        printf("%s\n", :::no-loc(__func__):::);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Macros prédéfinies standard

Le compilateur prend en charge ces macros prédéfinies spécifiées par les normes ISO C99 et ISO 17 ISO 17.

- `:::no-loc(__cplusplus):::`Défini en tant que valeur littérale entière lorsque l’unité de traduction est compilée en tant que C++. Sinon, non défini.

- `:::no-loc(__DATE__):::`Date de compilation du fichier source actuel. La date est un littéral de chaîne de longueur constante sous la forme *mmm jj aaaa*. Le nom du mois *MMM* est le même que le nom du mois abrégé généré par la fonction [asctime](../c-runtime-library/reference/asctime-wasctime.md) de la bibliothèque Runtime C (CRT). Le premier caractère de la date *JJ* est un espace si la valeur est inférieure à 10. Cette macro est toujours définie.

- `:::no-loc(__FILE__):::`Nom du fichier source actuel. `:::no-loc(__FILE__):::`se développe en un littéral de chaîne de caractères. Pour vous assurer que le chemin d’accès complet au fichier est affiché, utilisez [ **`/FC`** (chemin d’accès complet du fichier de code source dans les Diagnostics)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Cette macro est toujours définie.

- `:::no-loc(__LINE__):::`Défini en tant que numéro de ligne entière dans le fichier source actuel. La valeur de la `:::no-loc(__LINE__):::` macro peut être modifiée à l’aide d’une `#line` directive. Cette macro est toujours définie.

- `:::no-loc(__STDC__):::`Défini comme 1 uniquement lorsqu’il est compilé en tant que C et si l' [**`/Za`**](../build/reference/za-ze-disable-language-extensions.md) option de compilateur est spécifiée. Sinon, non défini.

- `:::no-loc(__STDC_HOSTED__):::`Défini comme 1 si l’implémentation est une *implémentation hébergée*, qui prend en charge l’intégralité de la bibliothèque standard requise. Dans le cas contraire, défini sur 0.

- `:::no-loc(__STDCPP_THREADS__):::`Défini comme 1 si et seulement si un programme peut avoir plusieurs threads d’exécution et compilé en C++. Sinon, non défini.

- `:::no-loc(__TIME__):::`Heure de la traduction de l’unité de traduction prétraitée. L’heure est un littéral de chaîne de caractères au format *hh : mm : SS*, le même que le temps retourné par la fonction CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md) . Cette macro est toujours définie.

## <a name="microsoft-specific-predefined-macros"></a>Macros prédéfinies spécifiques à Microsoft

MSVC prend en charge ces macros prédéfinies supplémentaires.

- `:::no-loc(__ATOM__):::`Défini comme 1 lorsque l' [**`/favor:ATOM`**](../build/reference/favor-optimize-for-architecture-specifics.md) option de compilateur est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- `:::no-loc(__AVX__):::`Défini comme 1 lorsque les [**`/arch:AVX`**](../build/reference/arch-x86.md) [**`/arch:AVX2`**](../build/reference/arch-x86.md) [**`/arch:AVX512`**](../build/reference/arch-x86.md) Options du compilateur, ou sont définies et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- `:::no-loc(__AVX2__):::`Défini comme 1 lorsque l' [**`/arch:AVX2`**](../build/reference/arch-x86.md) [**`/arch:AVX512`**](../build/reference/arch-x86.md) option du compilateur ou est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- `:::no-loc(__AVX512BW__):::`Défini comme 1 lorsque l' [**`/arch:AVX512`**](../build/reference/arch-x86.md) option de compilateur est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- `:::no-loc(__AVX512CD__):::`Défini comme 1 lorsque l' [**`/arch:AVX512`**](../build/reference/arch-x86.md) option de compilateur est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- `:::no-loc(__AVX512DQ__):::`Défini comme 1 lorsque l' [**`/arch:AVX512`**](../build/reference/arch-x86.md) option de compilateur est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- `:::no-loc(__AVX512F__):::`Défini comme 1 lorsque l' [**`/arch:AVX512`**](../build/reference/arch-x86.md) option de compilateur est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- `:::no-loc(__AVX512VL__):::`Défini comme 1 lorsque l' [**`/arch:AVX512`**](../build/reference/arch-x86.md) option de compilateur est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- `:::no-loc(_CHAR_UNSIGNED):::`Défini comme 1 si le type par défaut **`char`** est non signé. Cette valeur est définie lorsque l’option [ **`/J`** de compilateur (type de caractère par défaut est non signé)](../build/reference/j-default-char-type-is-unsigned.md) est définie. Sinon, non défini.

- `:::no-loc(__CLR_VER):::`Défini comme un littéral entier qui représente la version du Common Language Runtime (CLR) utilisée pour compiler l’application. La valeur est encodée sous la forme `Mmmbbbbb` , où `M` est la version principale du runtime, `mm` est la version mineure du runtime et `bbbbb` est le numéro de Build. `:::no-loc(__CLR_VER):::`est défini si l' [**`/clr`**](../build/reference/clr-common-language-runtime-compilation.md) option de compilateur est définie. Sinon, non défini.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(:::no-loc(__CLR_VER):::);
    }
    ```

- `:::no-loc(_CONTROL_FLOW_GUARD):::`Défini comme 1 lorsque l’option [ **`/guard:cf`** de compilateur (activer le garde de contrôle du Workflow)](../build/reference/guard-enable-control-flow-guard.md) est définie. Sinon, non défini.

- `:::no-loc(__COUNTER__):::`Se développe en un littéral d’entier qui commence à 0. La valeur est incrémentée de 1 chaque fois qu’elle est utilisée dans un fichier source ou dans les en-têtes inclus du fichier source. `:::no-loc(__COUNTER__):::` conserve son état lorsque vous utilisez des en-têtes précompilés. Cette macro est toujours définie.

  Cet exemple utilise `:::no-loc(__COUNTER__):::` pour assigner des identificateurs uniques à trois objets différents du même type. Le `exampleClass` constructeur prend un entier comme paramètre. Dans `main` , l’application déclare trois objets de type `exampleClass` , en utilisant `:::no-loc(__COUNTER__):::` comme paramètre d’identificateur unique :

    ```cpp
    // macro:::no-loc(__COUNTER__):::.cpp
    // Demonstration of :::no-loc(__COUNTER__):::, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro:::no-loc(__COUNTER__):::.cpp
    #include <stdio.h>

    class exampleClass {
        int m_nID;
    public:
        // initialize object with a read-only unique ID
        exampleClass(int nID) : m_nID(nID) {}
        int GetID(void) { return m_nID; }
    };

    int main()
    {
        // :::no-loc(__COUNTER__)::: is initially defined as 0
        exampleClass e1(:::no-loc(__COUNTER__):::);

        // On the second reference, :::no-loc(__COUNTER__)::: is now defined as 1
        exampleClass e2(:::no-loc(__COUNTER__):::);

        // :::no-loc(__COUNTER__)::: is now defined as 2
        exampleClass e3(:::no-loc(__COUNTER__):::);

        printf("e1 ID: %i\n", e1.GetID());
        printf("e2 ID: %i\n", e2.GetID());
        printf("e3 ID: %i\n", e3.GetID());

        // Output
        // ------------------------------
        // e1 ID: 0
        // e2 ID: 1
        // e3 ID: 2

        return 0;
    }
    ```

- `:::no-loc(__cplusplus_cli):::`Défini en tant que valeur littérale entière 200406 en cas de compilation en C++ et une [**`/clr`**](../build/reference/clr-common-language-runtime-compilation.md) option de compilateur est définie. Sinon, non défini. En cas de définition, `:::no-loc(__cplusplus_cli):::` est activé dans toute l’unité de traduction.

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef :::no-loc(__cplusplus_cli):::
          printf("%d\n", :::no-loc(__cplusplus_cli):::);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- `:::no-loc(__cplusplus_winrt):::`Défini en tant que valeur littérale entière 201009 lorsqu’il est compilé en C++ et que l’option de compilateur [ **`/ZW`** (Windows Runtime Compilation)](../build/reference/zw-windows-runtime-compilation.md) est définie. Sinon, non défini.

- `:::no-loc(_CPPRTTI):::`Défini comme 1 si l’option [ **`/GR`** de compilateur (activer les informations de type au moment de l’exécution)](../build/reference/gr-enable-run-time-type-information.md) est définie. Sinon, non défini.

- `:::no-loc(_CPPUNWIND):::`Défini comme 1 si au moins une des options du compilateur ( [ **`/GX`** activer la gestion des exceptions)](../build/reference/gx-enable-exception-handling.md), [ **`/clr`** (compilation du Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)ou [ **`/EH`** (modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md) est définie. Sinon, non défini.

- `:::no-loc(_DEBUG):::`Défini comme 1 lorsque l' [**`/LDd`**](../build/reference/md-mt-ld-use-run-time-library.md) [**`/MDd`**](../build/reference/md-mt-ld-use-run-time-library.md) [**`/MTd`**](../build/reference/md-mt-ld-use-run-time-library.md) option du compilateur, ou est définie. Sinon, non défini.

- `:::no-loc(_DLL):::`Défini comme 1 lorsque l' [**`/MD`**](../build/reference/md-mt-ld-use-run-time-library.md) [**`/MDd`**](../build/reference/md-mt-ld-use-run-time-library.md) option de compilateur ou (DLL multithread) est définie. Sinon, non défini.

- `:::no-loc(__FUNCDNAME__):::`Défini en tant que littéral de chaîne qui contient le [nom décoré](../build/reference/decorated-names.md) de la fonction englobante. La macro est définie uniquement dans une fonction. La `:::no-loc(__FUNCDNAME__):::` macro n’est pas développée si vous utilisez l' [**`/EP`**](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) [**`/P`**](../build/reference/p-preprocess-to-a-file.md) option du compilateur ou.

   Cet exemple utilise les `:::no-loc(__FUNCDNAME__):::` `:::no-loc(__FUNCSIG__):::` `:::no-loc(__FUNCTION__):::` macros, et pour afficher des informations sur les fonctions.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- `:::no-loc(__FUNCSIG__):::`Défini en tant que littéral de chaîne qui contient la signature de la fonction englobante. La macro est définie uniquement dans une fonction. La `:::no-loc(__FUNCSIG__):::` macro n’est pas développée si vous utilisez l' [**`/EP`**](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) [**`/P`**](../build/reference/p-preprocess-to-a-file.md) option du compilateur ou. En cas de compilation pour une cible 64 bits, la Convention d’appel est **`__cdecl`** par défaut. Pour obtenir un exemple d’utilisation, consultez la `:::no-loc(__FUNCDNAME__):::` macro.

- `:::no-loc(__FUNCTION__):::`Défini en tant que littéral de chaîne qui contient le nom non décoré de la fonction englobante. La macro est définie uniquement dans une fonction. La `:::no-loc(__FUNCTION__):::` macro n’est pas développée si vous utilisez l' [**`/EP`**](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) [**`/P`**](../build/reference/p-preprocess-to-a-file.md) option du compilateur ou. Pour obtenir un exemple d’utilisation, consultez la `:::no-loc(__FUNCDNAME__):::` macro.

- `:::no-loc(_INTEGRAL_MAX_BITS):::`Défini en tant que valeur littérale entière 64, la taille maximale (en bits) d’un type intégral non vecteur. Cette macro est toujours définie.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", :::no-loc(_INTEGRAL_MAX_BITS):::);
   }
   ```

- `__INTELLISENSE__`Défini comme 1 pendant un compilateur IntelliSense passe dans l’IDE de Visual Studio. Sinon, non défini. Vous pouvez utiliser cette macro pour protéger le code que le compilateur IntelliSense ne comprend pas, ou l’utiliser pour basculer entre la génération et le compilateur IntelliSense. Pour plus d’informations, consultez [conseils de dépannage pour la lenteur d’IntelliSense](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/).

- `:::no-loc(_ISO_VOLATILE):::`Défini comme 1 si l' [**`/volatile:iso`**](../build/reference/volatile-volatile-keyword-interpretation.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(_KERNEL_MODE):::`Défini comme 1 si l’option [ **`/kernel`** de compilateur (créer un fichier binaire en mode noyau)](../build/reference/kernel-create-kernel-mode-binary.md) est définie. Sinon, non défini.

- `:::no-loc(_M_AMD64):::`Défini en tant que valeur littérale entière 100 pour les compilations qui ciblent des processeurs x64. Sinon, non défini.

- `:::no-loc(_M_ARM):::`Défini en tant que valeur littérale d’entier 7 pour les compilations qui ciblent des processeurs ARM. Sinon, non défini.

- `:::no-loc(_M_ARM_ARMV7VE):::`Défini comme 1 lorsque l' [**`/arch:ARMv7VE`**](../build/reference/arch-arm.md) option de compilateur est définie pour les compilations qui ciblent des processeurs ARM. Sinon, non défini.

- `:::no-loc(_M_ARM_FP):::`Défini en tant que valeur littérale entière indiquant l' [**`/arch`**](../build/reference/arch-arm.md) option de compilateur définie pour les cibles de processeur ARM. Sinon, non défini.

  - Valeur comprise dans la plage 30-39 si aucune **`/arch`** option ARM n’a été spécifiée, indiquant que l’architecture par défaut pour ARM a été définie ( `VFPv3` ).

  - Valeur comprise dans la plage 40-49 si **`/arch:VFPv4`** a été défini.

  - Pour plus d’informations, consultez [ **`/arch`** (ARM)](../build/reference/arch-arm.md).

- `:::no-loc(_M_ARM64):::`Défini comme 1 pour les compilations qui ciblent des processeurs ARM 64 bits. Sinon, non défini.

- `:::no-loc(_M_CEE):::`Défini comme 001 si une option du compilateur [ **`/clr`** (compilation du Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) est définie. Sinon, non défini.

- `:::no-loc(_M_CEE_PURE):::`Déconseillé depuis Visual Studio 2015. Défini comme 001 si l' [**`/clr:pure`**](../build/reference/clr-common-language-runtime-compilation.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(_M_CEE_SAFE):::`Déconseillé depuis Visual Studio 2015. Défini comme 001 si l' [**`/clr:safe`**](../build/reference/clr-common-language-runtime-compilation.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(_M_FP_EXCEPT):::`Défini comme 1 si l' [**`/fp:except`**](../build/reference/fp-specify-floating-point-behavior.md) [**`/fp:strict`**](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur ou est définie. Sinon, non défini.

- `:::no-loc(_M_FP_FAST):::`Défini comme 1 si l' [**`/fp:fast`**](../build/reference/fp-specify-floating-point-behavior.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(_M_FP_PRECISE):::`Défini comme 1 si l' [**`/fp:precise`**](../build/reference/fp-specify-floating-point-behavior.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(_M_FP_STRICT):::`Défini comme 1 si l' [**`/fp:strict`**](../build/reference/fp-specify-floating-point-behavior.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(_M_IX86):::`Défini en tant que valeur littérale entière 600 pour les compilations qui ciblent des processeurs x86. Cette macro n’est pas définie pour les cibles de compilation x64 ou ARM.

- `:::no-loc(_M_IX86_FP):::`Défini en tant que valeur littérale entière indiquant l' [**`/arch`**](../build/reference/arch-arm.md) option de compilateur qui a été définie, ou la valeur par défaut. Cette macro est toujours définie lorsque la cible de compilation est un processeur x86. Sinon, non défini. Lorsqu’elle est définie, la valeur est :

  - 0 si l' `/arch:IA32` option de compilateur a été définie.

  - 1 si l' `/arch:SSE` option de compilateur a été définie.

  - 2 si l' `/arch:SSE2` `/arch:AVX` option de compilateur,, `/arch:AVX2` ou `/arch:AVX512` a été définie. Cette valeur est la valeur par défaut si aucune `/arch` option du compilateur n’a été spécifiée. Lorsque `/arch:AVX` est spécifié, la macro `:::no-loc(__AVX__):::` est également définie. Lorsque `/arch:AVX2` est spécifié, `:::no-loc(__AVX__):::` et `:::no-loc(__AVX2__):::` sont également définis. Lorsque `/arch:AVX512` est spécifié,,,,,,, `:::no-loc(__AVX__):::` `:::no-loc(__AVX2__):::` `:::no-loc(__AVX512BW__):::` `:::no-loc(__AVX512CD__):::` `:::no-loc(__AVX512DQ__):::` `:::no-loc(__AVX512F__):::` et `:::no-loc(__AVX512VL__):::` sont également définis.

  - Pour plus d’informations, consultez [ **`/arch`** (x86)](../build/reference/arch-x86.md).

- `:::no-loc(_M_X64):::`Défini en tant que valeur littérale entière 100 pour les compilations qui ciblent des processeurs x64. Sinon, non défini.

- `:::no-loc(_MANAGED):::`Défini comme 1 lorsque l' [**`/clr`**](../build/reference/clr-common-language-runtime-compilation.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(_MSC_BUILD):::`Défini comme un littéral d’entier qui contient l’élément de numéro de révision du numéro de version du compilateur. Le numéro de révision est le quatrième élément du numéro de version délimité par des points. Par exemple, si le numéro de version du compilateur Microsoft C/C++ est 15.00.20706.01, la `:::no-loc(_MSC_BUILD):::` macro prend la valeur 1. Cette macro est toujours définie.

- `:::no-loc(_MSC_EXTENSIONS):::`Défini comme 1 si l’option de compilateur activé par défaut [ **`/Ze`** (activer les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est définie. Sinon, non défini.

- `:::no-loc(_MSC_FULL_VER):::`Défini comme un littéral entier qui encode les éléments de numéro principal, secondaire et de build du numéro de version du compilateur. Le numéro principal est le premier élément du numéro de version délimité par des points, le nombre secondaire est le deuxième élément et le numéro de build est le troisième élément. Par exemple, si le numéro de version du compilateur Microsoft C/C++ est 15.00.20706.01, la `:::no-loc(_MSC_FULL_VER):::` macro prend la valeur 150020706. Entrez `cl /?` sur la ligne de commande pour afficher le numéro de version du compilateur. Cette macro est toujours définie.

- `:::no-loc(_MSC_VER):::`Défini comme un littéral d’entier qui encode les éléments de nombre majeurs et mineurs du numéro de version du compilateur. Le numéro principal est le premier élément du numéro de version délimité par des points et le nombre secondaire est le deuxième élément. Par exemple, si le numéro de version du compilateur Microsoft C/C++ est 17.00.51106.1, la `:::no-loc(_MSC_VER):::` macro prend la valeur 1700. Entrez `cl /?` sur la ligne de commande pour afficher le numéro de version du compilateur. Cette macro est toujours définie.

   | Version de Visual Studio | `:::no-loc(_MSC_VER):::` |
   |--|--|
   | Visual Studio 6.0 | 1200 |
   | Visual Studio .NET 2002 (7,0) | 1 300 |
   | Visual Studio .NET 2003 (7,1) | 1310 |
   | Visual Studio 2005 (8,0) | 1400 |
   | Visual Studio 2008 (9,0) | 1500 |
   | Visual Studio 2010 (10,0) | 1 600 |
   | Visual Studio 2012 (11,0) | 1 700 |
   | Visual Studio 2013 (12,0) | 1800 |
   | Visual Studio 2015 (14,0) | 1900 |
   | Visual Studio 2017 RTW (15,0) | 1910 |
   | Visual Studio 2017 version 15.3 | 1911 |
   | Visual Studio 2017 version 15.5 | 1912 |
   | Visual Studio 2017 version 15.6 | 1913 |
   | Visual Studio 2017 version 15.7 | 1914 |
   | Visual Studio 2017 version 15.8 | 1915 |
   | Visual Studio 2017 version 15,9 | 1916 |
   | Visual Studio 2019 RTW (16,0) | 1920 |
   | Visual Studio 2019 version 16.1 | 1921 |
   | Visual Studio 2019 version 16.2 | 1922 |
   | Visual Studio 2019 version 16,3 | 1923 |
   |  Visual Studio 2019 version 16.4 | 1924 |
   | Visual Studio 2019 version 16,5 | 1925 |
   | Visual Studio 2019 version 16,6 | 1926 |
   | Visual Studio 2019 version 16,7 | 1927 |

   Pour tester les mises à jour ou les mises à jour du compilateur dans une version donnée de Visual Studio ou après, utilisez l' `>=` opérateur. Vous pouvez l’utiliser dans une directive conditionnelle pour effectuer une comparaison `:::no-loc(_MSC_VER):::` par rapport à cette version connue. Si vous disposez de plusieurs versions mutuellement exclusives à comparer, Organisez vos comparaisons dans l’ordre décroissant du numéro de version. Par exemple, ce code recherche les compilateurs publiés dans Visual Studio 2017 et versions ultérieures. Ensuite, il recherche les compilateurs publiés dans ou après Visual Studio 2015. Il vérifie ensuite tous les compilateurs publiés avant Visual Studio 2015 :

   ```cpp
   #if :::no-loc(_MSC_VER)::: >= 1910
   // . . .
   #elif :::no-loc(_MSC_VER)::: >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   Pour plus d’informations, consultez [Visual C++ version du compilateur](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) dans le blog de l’équipe Microsoft C++.

- `:::no-loc(_MSVC_LANG):::`Défini comme un littéral entier qui spécifie la norme du langage C++ ciblée par le compilateur. Elle est définie uniquement dans le code compilé en C++. La macro est la valeur littérale entière 201402L par défaut, ou lorsque l' [**`/std:c++14`**](../build/reference/std-specify-language-standard-version.md) option de compilateur est spécifiée. La macro est définie sur 201703L si l' [**`/std:c++17`**](../build/reference/std-specify-language-standard-version.md) option de compilateur est spécifiée. Elle est définie sur une valeur plus élevée, non spécifiée, lorsque l' [**`/std:c++latest`**](../build/reference/std-specify-language-standard-version.md) option est spécifiée. Dans le cas contraire, la macro n’est pas définie. Les `:::no-loc(_MSVC_LANG):::` options de compilateur macro et [ **`/std`** (spécifier la version du langage standard)](../build/reference/std-specify-language-standard-version.md) sont disponibles à partir de Visual Studio 2015 Update 3.

- `:::no-loc(__MSVC_RUNTIME_CHECKS):::`Défini comme 1 lorsque l’une des [**`/RTC`**](../build/reference/rtc-run-time-error-checks.md) Options du compilateur est définie. Sinon, non défini.

- `_MSVC_TRADITIONAL`Défini comme 0 lorsque l’option de compilateur du mode de conformité du préprocesseur [**`/experimental:preprocessor`**](../build/reference/experimental-preprocessor.md) est définie. Défini comme 1 par défaut, ou lorsque l' [**`/experimental:preprocessor-`**](../build/reference/experimental-preprocessor.md) option de compilateur est définie, pour indiquer que le préprocesseur traditionnel est en cours d’utilisation. L' `_MSVC_TRADITIONAL` option de compilateur macro et [ **`/experimental:preprocessor`** (activer le mode de conformité de préprocesseur)](../build/reference/experimental-preprocessor.md) est disponible à partir de Visual Studio 2017 version 15,8.

   ```cpp
   #if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
   // Logic using the traditional preprocessor
   #else
   // Logic using cross-platform compatible preprocessor
   #endif
   ```

- `:::no-loc(_MT):::`Défini comme 1 lorsque [ **`/MD`** ou **`/MDd`** (DLL multithread)](../build/reference/md-mt-ld-use-run-time-library.md) ou [ **`/MT`** ou **`/MTd`** (multithread)](../build/reference/md-mt-ld-use-run-time-library.md) est spécifié. Sinon, non défini.

- `:::no-loc(_NATIVE_WCHAR_T_DEFINED):::`Défini comme 1 lorsque l' [**`/Zc:wchar_t`**](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(_OPENMP):::`Défini en tant que littéral entier 200203, si l’option [ **`/openmp`** de compilateur (activer la prise en charge OpenMP 2,0)](../build/reference/openmp-enable-openmp-2-0-support.md) est définie. Cette valeur représente la date de la spécification OpenMP implémentée par MSVC. Sinon, non défini.

   ```cpp
   // :::no-loc(_OPENMP):::_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", :::no-loc(_OPENMP):::);
   }
   ```

- `:::no-loc(_PREFAST_):::`Défini comme 1 lorsque l' [**`/analyze`**](../build/reference/analyze-code-analysis.md) option de compilateur est définie. Sinon, non défini.

- `:::no-loc(__TIMESTAMP__):::`Défini en tant que littéral de chaîne qui contient la date et l’heure de la dernière modification du fichier source actuel, dans la forme abrégée de longueur constante retournée par la [`asctime`](../c-runtime-library/reference/asctime-wasctime.md) fonction CRT, par exemple, `Fri 19 Aug 13:32:58 2016` . Cette macro est toujours définie.

- `:::no-loc(_VC_NODEFAULTLIB):::`Défini comme 1 lorsque l’option [ **`/Zl`** de compilateur (omettre le nom de la bibliothèque par défaut)](../build/reference/zl-omit-default-library-name.md) est définie. Sinon, non défini.

- `:::no-loc(_WCHAR_T_DEFINED):::`Défini comme 1 lorsque l’option de compilateur par défaut [**`/Zc:wchar_t`**](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) est définie. La `:::no-loc(_WCHAR_T_DEFINED):::` macro est définie, mais elle n’a pas de valeur si l' **`/Zc:wchar_t-`** option de compilateur est définie et **`wchar_t`** est définie dans un fichier d’en-tête système inclus dans votre projet. Sinon, non défini.

- `:::no-loc(_WIN32):::`Défini comme 1 lorsque la cible de compilation est 32-bit ARM, 64 bits ARM, x86 ou x64. Sinon, non défini.

- `:::no-loc(_WIN64):::`Défini comme 1 lorsque la cible de compilation est 64 bits ARM ou x64. Sinon, non défini.

- `:::no-loc(_WINRT_DLL):::`Défini comme 1 en cas de compilation en C++ et les deux [ **`/ZW`** (Windows Runtime Compilation)](../build/reference/zw-windows-runtime-compilation.md) [ **`/LD`** **`/LDd`** ](../build/reference/md-mt-ld-use-run-time-library.md) et les options de compilateur sont définies. Sinon, non défini.

Aucune macro de préprocesseur qui identifie la version de la bibliothèque ATL ou MFC n’est prédéfinie par le compilateur. Les en-têtes de bibliothèque ATL et MFC définissent ces macros de version en interne. Elles ne sont pas définies dans les directives de préprocesseur effectuées avant l’inclusion de l’en-tête requis.

- `:::no-loc(_ATL_VER):::`Défini dans \<atldef.h> en tant que littéral entier qui encode le numéro de version ATL.

- `:::no-loc(_MFC_VER):::`Défini dans \<afxver_.h> en tant que littéral entier qui encode le numéro de version MFC.

## <a name="see-also"></a>Voir aussi

[Macros (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)<br/>
[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
