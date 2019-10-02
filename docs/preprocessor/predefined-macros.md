---
title: Macros prédéfinies
ms.custom: update_every_version
ms.date: 10/01/2019
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- __AVX512BW__
- __AVX512CD__
- __AVX512DQ__
- __AVX512F__
- __AVX512VL__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- __AVX512BW__ macro
- __AVX512CD__ macro
- __AVX512DQ__ macro
- __AVX512F__ macro
- __AVX512VL__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
ms.openlocfilehash: eb75273bc8cbe5ccbf62edc82a1e7deccc605757
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816603"
---
# <a name="predefined-macros"></a>Macros prédéfinies

Le compilateur Microsoft CC++ /(MSVC) prédéfinit certaines macros de préprocesseur, en fonction du langage (C ou C++), de la cible de compilation et des options de compilateur choisies.

MSVC prend en charge les macros de préprocesseur prédéfinies requises par les normes ANSI/ISO C99 standard et ISO C++ 14 et C++ 17. L’implémentation prend également en charge plusieurs macros de préprocesseur spécifiques à Microsoft. Certaines macros sont définies uniquement pour des environnements de génération ou des options de compilateur spécifiques. Sauf mention contraire, les macros sont définies dans toute l’unité de traduction comme si elles étaient spécifiées comme des arguments de l’option de compilateur **/d** . Lorsqu’elles sont définies, les macros sont développées aux valeurs spécifiées par le préprocesseur avant la compilation. Les macros prédéfinies ne prennent pas d’arguments et ne peuvent pas être redéfinies.

## <a name="standard-predefined-identifier"></a>Identificateur prédéfini standard

Le compilateur prend en charge cet identificateur prédéfini spécifié par ISO C99 et ISO C++ 11.

- **&#95; Func &#95; &#95;** Nom non qualifié et sans ornement de la fonction englobante en tant que tableau **statique const statique** de fonction de **type char**.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Macros prédéfinies standard

Le compilateur prend en charge ces macros prédéfinies spécifiées par les normes ISO C99 et ISO 17 ISO 17.

- **&#95;Cplusplus &#95;** Défini en tant que valeur littérale entière lorsque l’unité de traduction C++est compilée comme. Sinon, non défini.

- **&#95; Date &#95; &#95;** Date de compilation du fichier source actuel. La date est un littéral de chaîne de longueur constante sous la forme *mmm jj aaaa*. Le nom du mois *MMM* est le même que le nom du mois abrégé généré par la fonction [asctime](../c-runtime-library/reference/asctime-wasctime.md) de la bibliothèque Runtime C (CRT). Le premier caractère de la date *JJ* est un espace si la valeur est inférieure à 10. Cette macro est toujours définie.

- **&#95; Fichier &#95; &#95;** Nom du fichier source actuel. Le fichier se développe en un littéral de chaîne de caractères. **&#95; &#95;&#95;** Pour vous assurer que le chemin d’accès complet au fichier s’affiche, utilisez [/FC (chemin d’accès complet du fichier de code source dans les Diagnostics)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Cette macro est toujours définie.

- **&#95; Ligne &#95; &#95;** Défini en tant que numéro de ligne entière dans le fichier source actuel. La valeur de la  **&#95; &#95;macro&#95; de ligne** peut être modifiée à l’aide d’une directive `#line`. Cette macro est toujours définie.

- **&#95; STDC &#95; &#95;** Défini comme 1 uniquement lorsqu’il est compilé en tant que C et si l’option de compilateur [/za](../build/reference/za-ze-disable-language-extensions.md) est spécifiée. Sinon, non défini.

- **&#95;&#95;STDC&#95;hébergé&#95;**  défini comme 1 si l’implémentation est une *implémentation hébergée*, qui prend en charge l’intégralité de la bibliothèque standard requise. Dans le cas contraire, défini sur 0.

- **&#95;&#95;&#95;Threads&#95; STDCPP** définis comme 1 si et seulement si un programme peut avoir plusieurs threads d’exécution et compilé comme. C++ Sinon, non défini.

- **&#95; Heure &#95; &#95;** Heure de la traduction de l’unité de traduction prétraitée. L’heure est un littéral de chaîne de caractères au format *hh : mm : SS*, le même que le temps retourné par la fonction CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md) . Cette macro est toujours définie.

## <a name="microsoft-specific-predefined-macros"></a>Macros prédéfinies spécifiques à Microsoft

MSVC prend en charge ces macros prédéfinies supplémentaires.

- **&#95; Atom &#95; &#95;** Défini comme 1 lorsque l’option de compilateur [/favor : Atom](../build/reference/favor-optimize-for-architecture-specifics.md) est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95; AVX &#95; &#95;** Défini comme 1 lorsque les options de compilateur [/arch : AVX](../build/reference/arch-x86.md), [/arch : AVX2](../build/reference/arch-x86.md) ou [/arch : AVX512](../build/reference/arch-x86.md) sont définies et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95; AVX2 &#95; &#95;** Défini comme 1 lorsque l’option de compilateur [/arch : AVX2](../build/reference/arch-x86.md) ou [/arch : AVX512](../build/reference/arch-x86.md) est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95; AVX512BW &#95; &#95;** Défini comme 1 lorsque l’option de compilateur [/arch : AVX512](../build/reference/arch-x86.md) est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95; AVX512CD &#95; &#95;** Défini comme 1 lorsque l’option de compilateur [/arch : AVX512](../build/reference/arch-x86.md) est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95; AVX512DQ &#95; &#95;** Défini comme 1 lorsque l’option de compilateur [/arch : AVX512](../build/reference/arch-x86.md) est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95; AVX512F &#95; &#95;** Défini comme 1 lorsque l’option de compilateur [/arch : AVX512](../build/reference/arch-x86.md) est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95; AVX512VL &#95; &#95;** Défini comme 1 lorsque l’option de compilateur [/arch : AVX512](../build/reference/arch-x86.md) est définie et que la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95;CHAR&#95;non signé** défini comme 1 si le type de **caractère** par défaut est non signé. Cette valeur est définie lorsque l’option de compilateur [/j (type de caractère par défaut est non signé)](../build/reference/j-default-char-type-is-unsigned.md) est définie. Sinon, non défini.

- **&#95;&#95;ver &#95;CLR** Défini comme un littéral entier qui représente la version du Common Language Runtime (CLR) utilisée pour compiler l’application. La valeur est encodée sous la forme `Mmmbbbbb`, où `M` est la version principale du runtime, `mm` est la version mineure du runtime et `bbbbb` est le numéro de Build. **&#95;&#95;CLR&#95;ver** est défini si l’option du compilateur [/CLR](../build/reference/clr-common-language-runtime-compilation.md) est définie. Sinon, non défini.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;Protection&#95;du&#95;workflow de contrôle** définie comme 1 lorsque l’option de compilateur [/Guard : CF (activer la protection du workflow de contrôle)](../build/reference/guard-enable-control-flow-guard.md) est définie. Sinon, non défini.

- **&#95; Compteur &#95; &#95;** Se développe en un littéral d’entier qui commence à 0. La valeur est incrémentée de 1 chaque fois qu’elle est utilisée dans un fichier source ou dans les en-têtes inclus du fichier source. Le compteur mémorise son état lorsque vous utilisez des en-têtes précompilés. **&#95; &#95;&#95;** Cette macro est toujours définie.

  Cet exemple utilise `__COUNTER__` pour assigner des identificateurs uniques à trois objets différents du même type. Le constructeur `exampleClass` accepte un entier comme paramètre. Dans `main`, l’application déclare trois objets de type `exampleClass`, en utilisant `__COUNTER__` comme paramètre d’identificateur unique :

    ```cpp
    // macro__COUNTER__.cpp
    // Demonstration of __COUNTER__, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp
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
        // __COUNTER__ is initially defined as 0
        exampleClass e1(__COUNTER__);

        // On the second reference, __COUNTER__ is now defined as 1
        exampleClass e2(__COUNTER__);

        // __COUNTER__ is now defined as 2
        exampleClass e3(__COUNTER__);

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

- **&#95;&#95;Cplusplus&#95;CLI** définie en tant que valeur littérale entière 200406 quand C++ elle est compilée en tant que et qu’une option de compilateur [/CLR](../build/reference/clr-common-language-runtime-compilation.md) est définie. Sinon, non défini. Lorsqu’elle est définie,  **&#95; &#95;l’interface de commande Cplusplus&#95;** est en vigueur dans toute l’unité de traduction.

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef __cplusplus_cli
          printf("%d\n", __cplusplus_cli);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- **&#95;&#95;Cplusplus&#95;WinRT** défini en tant que valeur littérale entière 201009 lorsqu' C++ il est compilé en tant que et que l’option de compilateur [/ZW (Windows Runtime Compilation)](../build/reference/zw-windows-runtime-compilation.md) est définie. Sinon, non défini.

- **&#95;CPPRTTI** Défini comme 1 si l’option de compilateur [/gr (activer les informations de type au moment de l’exécution)](../build/reference/gr-enable-run-time-type-information.md) est définie. Sinon, non défini.

- **&#95;CPPUNWIND** Défini comme 1 si une ou plusieurs des options de compilateur [/GX (activer la gestion des exceptions)](../build/reference/gx-enable-exception-handling.md), [/clr (compilation du Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)ou [/Eh (modèle de gestion des exceptions)](../build/reference/eh-exception-handling-model.md) sont définies. Sinon, non défini.

- **&#95;Débogage** Défini comme 1 lorsque l’option de compilateur [/LDD](../build/reference/md-mt-ld-use-run-time-library.md), [/MDD](../build/reference/md-mt-ld-use-run-time-library.md)ou [/MTD](../build/reference/md-mt-ld-use-run-time-library.md) est définie. Sinon, non défini.

- DLL définie comme 1 lorsque l’option de compilateur [/MD](../build/reference/md-mt-ld-use-run-time-library.md) ou [/MDD](../build/reference/md-mt-ld-use-run-time-library.md) (DLL multithread) est définie.  **&#95;** Sinon, non défini.

- **&#95; FUNCDNAME &#95; &#95;** Défini en tant que littéral de chaîne qui contient le [nom décoré](../build/reference/decorated-names.md) de la fonction englobante. La macro est définie uniquement dans une fonction. **&#95;La &#95;macro&#95; FUNCDNAME** n’est pas développée si vous utilisez l’option de compilateur [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/p](../build/reference/p-preprocess-to-a-file.md) .

   Cet exemple utilise les macros `__FUNCDNAME__`, `__FUNCSIG__` et `__FUNCTION__` pour afficher les informations de fonction.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95; FUNCSIG &#95; &#95;** Défini en tant que littéral de chaîne qui contient la signature de la fonction englobante. La macro est définie uniquement dans une fonction. **&#95;La &#95;macro&#95; FUNCSIG** n’est pas développée si vous utilisez l’option de compilateur [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/p](../build/reference/p-preprocess-to-a-file.md) . En cas de compilation pour une cible 64 bits, la Convention d’appel est `__cdecl` par défaut. Pour obtenir un exemple d’utilisation, consultez la macro `__FUNCDNAME__`.

- **&#95; Fonction &#95; &#95;** Défini en tant que littéral de chaîne qui contient le nom non décoré de la fonction englobante. La macro est définie uniquement dans une fonction. La macro de  **&#95; &#95;&#95; fonction** n’est pas développée si vous utilisez l’option de compilateur [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/p](../build/reference/p-preprocess-to-a-file.md) . Pour obtenir un exemple d’utilisation, consultez la macro `__FUNCDNAME__`.

- **nombre d'&#95;octets max. intégral&#95; &#95;** Défini en tant que valeur littérale entière 64, la taille maximale (en bits) d’un type intégral non vecteur. Cette macro est toujours définie.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95; INTELLISENSE &#95; &#95;** Défini comme 1 pendant un compilateur IntelliSense passe dans l’IDE de Visual Studio. Sinon, non défini. Vous pouvez utiliser cette macro pour protéger le code que le compilateur IntelliSense ne comprend pas, ou l’utiliser pour basculer entre la génération et le compilateur IntelliSense. Pour plus d’informations, consultez [conseils de dépannage pour la lenteur d’IntelliSense](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;volatile** définie comme 1 si l’option de compilateur [/volatile : ISO](../build/reference/volatile-volatile-keyword-interpretation.md) est définie. Sinon, non défini.

- **&#95;MODE&#95;noyau** défini sur 1 si l’option de compilateur [/kernel (créer un fichier binaire en mode noyau)](../build/reference/kernel-create-kernel-mode-binary.md) est définie. Sinon, non défini.

- **&#95;C&#95;amd64** Défini en tant que valeur littérale entière 100 pour les compilations qui ciblent des processeurs x64. Sinon, non défini.

- **&#95;M&#95;bras** Défini en tant que valeur littérale d’entier 7 pour les compilations qui ciblent des processeurs ARM. Sinon, non défini.

- **&#95;M&#95;ARM&#95;ARMV7VE** défini comme 1 lorsque l’option de compilateur [/arch : ARMV7VE](../build/reference/arch-arm.md) est définie pour les compilations qui ciblent des processeurs ARM. Sinon, non défini.

- **&#95;M&#95;ARM&#95;FP** défini en tant que valeur littérale entière indiquant l’option de compilateur [/ARCH](../build/reference/arch-arm.md) définie pour les cibles de processeur ARM. Sinon, non défini.

  - Valeur comprise dans la plage 30-39 si aucune option ARM `/arch` n’a été spécifiée, indiquant que l’architecture par défaut pour ARM a été définie (`VFPv3`).

  - Valeur comprise dans la plage 40-49 si `/arch:VFPv4` a été défini.

  - Pour plus d’informations, consultez [/Arch (ARM)](../build/reference/arch-arm.md).

- **&#95;M&#95;ARM64** Défini comme 1 pour les compilations qui ciblent des processeurs ARM 64 bits. Sinon, non défini.

- **&#95;R&#95;CEE** défini comme 001 si une option de compilateur [/clr (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) est définie. Sinon, non défini.

- **r&#95;CEE&#95;pur &#95;** Déconseillé depuis Visual Studio 2015. Défini comme 001 si l’option de compilateur [/clr : pure](../build/reference/clr-common-language-runtime-compilation.md) est définie. Sinon, non défini.

- **r&#95;CEE&#95;- &#95;Safe** Déconseillé depuis Visual Studio 2015. Défini comme 001 si l’option de compilateur [/clr : safe](../build/reference/clr-common-language-runtime-compilation.md) est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;, sauf** défini comme 1 si l’option de compilateur [/FP : except](../build/reference/fp-specify-floating-point-behavior.md) ou [/FP : strict](../build/reference/fp-specify-floating-point-behavior.md) est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;défini rapidement** sur 1 si l’option de compilateur [/FP : Fast](../build/reference/fp-specify-floating-point-behavior.md) est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;precis** défini comme 1 si l’option de compilateur [/FP : precise](../build/reference/fp-specify-floating-point-behavior.md) est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;strict** défini sur 1 si l’option de compilateur [/FP : strict](../build/reference/fp-specify-floating-point-behavior.md) est définie. Sinon, non défini.

- **&#95;M&#95;ix86** Défini en tant que valeur littérale entière 600 pour les compilations qui ciblent des processeurs x86. Cette macro n’est pas définie pour les cibles de compilation x64 ou ARM.

- **&#95;M&#95;ix86&#95;FP** défini en tant que valeur littérale entière indiquant l’option de compilateur [/ARCH](../build/reference/arch-arm.md) qui a été définie, ou la valeur par défaut. Cette macro est toujours définie lorsque la cible de compilation est un processeur x86. Sinon, non défini. Lorsqu’elle est définie, la valeur est :

  - 0 si l’option du compilateur `/arch:IA32` a été définie.

  - 1 si l’option du compilateur `/arch:SSE` a été définie.

  - 2 si l’option de compilateur `/arch:SSE2`, `/arch:AVX`, `/arch:AVX2` ou `/arch:AVX512` a été définie. Cette valeur est la valeur par défaut si aucune option du compilateur `/arch` n’a été spécifiée. Lorsque `/arch:AVX` est spécifié, la macro **&#95; &#95;AVX&#95;** est également définie. Lorsque `/arch:AVX2` est spécifié, **&#95; &#95;AVX&#95;** et **&#95; &#95;AVX2&#95;** sont également définis. Lorsque `/arch:AVX512` est spécifié,  **&#95; &#95;AVX&#95;** ,  **&#95; &#95;AVX2&#95;** ,  **&#95; &#95;AVX512BW&#95;** ,  **&#95;&#95;AVX512CD, &#95;**  **&#95;AVX512DQ&#95;, &#95;** **AVX512F&#95; AVX512VL sont également définis. &#95; &#95;** **&#95; &#95;&#95;**

  - Pour plus d’informations, consultez l’article [/arch (x86)](../build/reference/arch-x86.md).

- **&#95;M&#95;x64** Défini en tant que valeur littérale entière 100 pour les compilations qui ciblent des processeurs x64. Sinon, non défini.

- **&#95;Géré** Défini comme 1 lorsque l’option du compilateur [/CLR](../build/reference/clr-common-language-runtime-compilation.md) est définie. Sinon, non défini.

- **&#95;Build&#95;MSC** Défini comme un littéral d’entier qui contient l’élément de numéro de révision du numéro de version du compilateur. Le numéro de révision est le quatrième élément du numéro de version délimité par des points. Par exemple, si le numéro de version du compilateur Microsoft CC++ /est 15.00.20706.01, la macro de  **&#95;génération MSC&#95;** prend la valeur 1. Cette macro est toujours définie.

- **&#95;EXTENSIONS&#95;MSC** définies sur 1 si l’option de compilateur [/Ze (activer les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) activée par défaut est définie. Sinon, non défini.

- **version complète&#95;MSC&#95; &#95;** Défini comme un littéral entier qui encode les éléments de numéro principal, secondaire et de build du numéro de version du compilateur. Le numéro principal est le premier élément du numéro de version délimité par des points, le nombre secondaire est le deuxième élément et le numéro de build est le troisième élément. Par exemple, si le numéro de version du compilateur Microsoft CC++ /est 15.00.20706.01, la macro version  **&#95;complète&#95;&#95;MSC** prend la valeur 150020706. Entrez `cl /?` sur la ligne de commande pour afficher le numéro de version du compilateur. Cette macro est toujours définie.

- **&#95;ver&#95;MSC** Défini comme un littéral d’entier qui encode les éléments de nombre majeurs et mineurs du numéro de version du compilateur. Le numéro principal est le premier élément du numéro de version délimité par des points et le nombre secondaire est le deuxième élément. Par exemple, si le numéro de version du compilateur Microsoft CC++ /est 17.00.51106.1, la  **&#95;macro&#95;MSC ver** prend la valeur 1700. Entrez `cl /?` sur la ligne de commande pour afficher le numéro de version du compilateur. Cette macro est toujours définie.

   |Version de Visual Studio|**&#95;MSC&#95;VER**|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7,0)|1300|
   |Visual Studio .NET 2003 (7,1)|1310|
   |Visual Studio 2005 (8,0)|1400|
   |Visual Studio 2008 (9,0)|1500|
   |Visual Studio 2010 (10,0)|1600|
   |Visual Studio 2012 (11,0)|1700|
   |Visual Studio 2013 (12,0)|1800|
   |Visual Studio 2015 (14,0)|1900|
   |Visual Studio 2017 RTW (15,0)|1910|
   |Visual Studio 2017 version 15.3|1911|
   |Visual Studio 2017 version 15.5|1912|
   |Visual Studio 2017 version 15.6|1913|
   |Visual Studio 2017 version 15.7|1914|
   |Visual Studio 2017 version 15.8|1915|
   |Visual Studio 2017 version 15,9|1916|
   |Visual Studio 2019 RTW (16,0)|1920|
   |Visual Studio 2019 version 16.1|1921|
   |Visual Studio 2019 version 16.2|1922|
   |Visual Studio 2019 version 16,3|1923|

   Pour tester les mises à jour ou les mises à jour du compilateur dans une version donnée de Visual Studio ou après, utilisez l’opérateur **>=** . Vous pouvez l’utiliser dans une directive conditionnelle pour comparer  **&#95;la&#95;** version de MSC à cette version connue. Si vous disposez de plusieurs versions mutuellement exclusives à comparer, Organisez vos comparaisons dans l’ordre décroissant du numéro de version. Par exemple, ce code recherche les compilateurs publiés dans Visual Studio 2017 et versions ultérieures. Ensuite, il recherche les compilateurs publiés dans ou après Visual Studio 2015. Il vérifie ensuite tous les compilateurs publiés avant Visual Studio 2015 :

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   Pour plus d’informations, [consultez C++ version du compilateur Visual](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) sur C++ le blog de l’équipe Microsoft.

- **&#95;MSVC&#95;lang** défini comme un littéral d’entier qui spécifie la C++ norme de langage ciblée par le compilateur. Elle est définie uniquement dans le code compilé C++en tant que. La macro est la valeur littérale entière 201402L par défaut, ou lorsque l’option de compilateur [/std : c++ 14](../build/reference/std-specify-language-standard-version.md) est spécifiée. La macro est définie sur 201703L si l’option de compilateur [/std : c++ 17](../build/reference/std-specify-language-standard-version.md) est spécifiée. Elle est définie sur une valeur plus élevée, non spécifiée lorsque l’option [/std : c + + latest](../build/reference/std-specify-language-standard-version.md) est spécifiée. Dans le cas contraire, la macro n’est pas définie. Les  **&#95;options&#95;de compilateur MSVC lang** macro et [/STD (Specify Language standard version)](../build/reference/std-specify-language-standard-version.md) sont disponibles à compter de Visual Studio 2015 Update 3.

- **&#95;&#95;Contrôles&#95;d'&#95;exécution MSVC** définis sur 1 lorsque l’une des options du compilateur [/RTC](../build/reference/rtc-run-time-error-checks.md) est définie. Sinon, non défini.

- **&#95;MSVC&#95;traditionnel** défini sur 0 lorsque le mode de conformité du préprocesseur/experimental : l’option du compilateur de [préprocesseur](../build/reference/rtc-run-time-error-checks.md) est définie. Défini par défaut sur 1, ou lorsque l’option [/experimental : preprocesseur-](../build/reference/rtc-run-time-error-checks.md) Compiler est définie, pour indiquer que le préprocesseur traditionnel est en cours d’utilisation. L'  **&#95;option&#95;** de compilateur macro traditionnelle MSVC et [/experimental : préprocesseur (activer le mode de conformité de préprocesseur)](../build/reference/experimental-preprocessor.md) est disponible à partir de Visual Studio 2017 version 15,8.

   ```cpp
   #if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
   // Logic using the traditional preprocessor
   #else
   // Logic using cross-platform compatible preprocessor
   #endif
   ```

- **&#95;MT** Défini comme 1 lorsque [/MD ou/MDD](../build/reference/md-mt-ld-use-run-time-library.md) (DLL multithread) ou [/MT ou/MTD](../build/reference/md-mt-ld-use-run-time-library.md) (multithread) est spécifié. Sinon, non défini.

- **&#95;&#95;WCHAR&#95;natif T&#95;défini** défini comme 1 lorsque l’option de compilateur [/Zc : wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) est définie. Sinon, non défini.

- **&#95;OpenMP** Défini en tant que littéral entier 200203, si l’option de compilateur [/openmp (activer la prise en charge openmp 2,0)](../build/reference/openmp-enable-openmp-2-0-support.md) est définie. Cette valeur représente la date de la spécification OpenMP implémentée par MSVC. Sinon, non défini.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREfast&#95;** Défini comme 1 lorsque l’option de compilateur [/analyze](../build/reference/analyze-code-analysis.md) est définie. Sinon, non défini.

- **&#95; Horodateur &#95; &#95;** Défini comme un littéral de chaîne qui contient la date et l’heure de la dernière modification du fichier source actuel, dans la forme abrégée de longueur constante retournée par la fonction CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md) , par exemple, `Fri 19 Aug 13:32:58 2016`. Cette macro est toujours définie.

- **&#95;VC&#95;NODEFAULTLIB (** défini comme 1 lorsque l’option de compilateur [/zl (omettre le nom de la bibliothèque par défaut)](../build/reference/zl-omit-default-library-name.md) est définie. Sinon, non défini.

- **&#95;WCHAR&#95;T&#95;défini** défini sur 1 lorsque l’option de compilateur [/Zc : wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) par défaut est définie. La  **&#95;macro&#95;définie&#95;par WCHAR T** est définie, mais elle n’a pas de valeur si l’option du compilateur `/Zc:wchar_t-` est définie et **wchar_t** est définie dans un fichier d’en-tête système inclus dans votre projet. Sinon, non défini.

- **&#95;Win32** Défini comme 1 lorsque la cible de compilation est 32-bit ARM, 64 bits ARM, x86 ou x64. Sinon, non défini.

- **&#95;Win64** Défini comme 1 lorsque la cible de compilation est 64 bits ARM ou x64. Sinon, non défini.

- **&#95;DLL&#95;WINRT** définie en tant que valeur 1 C++ lorsqu’elle est compilée en tant que et les deux options [/ZW (compilation Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) et [/LD ou/LDD](../build/reference/md-mt-ld-use-run-time-library.md) du compilateur sont définies. Sinon, non défini.

Aucune macro de préprocesseur qui identifie la version de la bibliothèque ATL ou MFC n’est prédéfinie par le compilateur. Les en-têtes de bibliothèque ATL et MFC définissent ces macros de version en interne. Elles ne sont pas définies dans les directives de préprocesseur effectuées avant l’inclusion de l’en-tête requis.

- **&#95;ATL&#95;ver** Défini dans \<atldef. h > sous la forme d’un littéral entier qui encode le numéro de version ATL.

- **&#95;MFC&#95;ver** Défini dans \<afxver_. h > sous la forme d’un littéral entier qui encode le numéro de version MFC.

## <a name="see-also"></a>Voir aussi

[Macros (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)<br/>
[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
