---
title: Macros prédéfinies
ms.custom: update_every_version
ms.date: 04/05/2019
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
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
ms.openlocfilehash: dedcab9b0addd3696749b50fef92b70081981c03
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237209"
---
# <a name="predefined-macros"></a>Macros prédéfinies

Le compilateur Microsoft C/C++ (MSVC) prédéfinit certaines macros de préprocesseur, selon la langue (C ou C++), la cible de compilation et les options de compilateur choisie.

MSVC prend en charge les macros de préprocesseur prédéfinis requis par la norme ANSI/ISO C99 et la norme ISO C ++ 14 et normes C ++ 17. L’implémentation prend également en charge plusieurs macros préprocesseur plus spécifiques à Microsoft. Certaines macros sont définies uniquement pour les environnements de génération spécifique ou les options du compilateur. Sauf mention contraire, les macros sont définies dans l’ensemble d’une unité de traduction comme s’ils ont été spécifiés en tant que **/D** arguments de l’option du compilateur. Lorsque défini, les macros sont développées pour les valeurs spécifiées par le préprocesseur avant la compilation. Les macros prédéfinies prennent aucun argument et ne peut pas être redéfinis.

## <a name="standard-predefined-identifier"></a>Identificateur prédéfini standard

Le compilateur prend en charge cet identificateur prédéfini spécifié par la norme ISO C99 et ISO C ++ 11.

- **&#95;&#95;Func&#95; &#95;**  le nom non qualifié et de la fonction englobante en tant que fonction local **statique const** tableau de **char**.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Macros prédéfinies standards

Le compilateur prend en charge ces macros prédéfinies spécifiés par la norme ISO C99 et C ++ 17 normes ISO.

- **&#95;&#95;cplusplus** définie comme une valeur littérale entière lors de l’unité de traduction est compilée en C++. Sinon, non défini.

- **&#95;&#95;DATE&#95; &#95;**  la date de la compilation du fichier source actuel. La date est une chaîne de longueur constante littérale du formulaire *Mmm jj aaaa*. Le nom du mois *Mmm* est le même que le nom de mois abrégé généré par la bibliothèque Runtime C (CRT) [asctime](../c-runtime-library/reference/asctime-wasctime.md) (fonction). Le premier caractère de date *jj* est un espace si la valeur est inférieure à 10. Cette macro est toujours définie.

- **&#95;&#95;FICHIER&#95; &#95;**  le nom du fichier source actuel. **&#95;&#95;FICHIER&#95; &#95;**  se développe en un littéral de chaîne de caractères. Pour vous assurer que le chemin d’accès complet au fichier s’affiche, utilisez [/FC (complet chemin d’accès du fichier de Code Source dans les Diagnostics)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Cette macro est toujours définie.

- **&#95;&#95;LIGNE&#95; &#95;**  défini comme le numéro de ligne entière dans le fichier source actuel. La valeur de la **&#95; &#95;ligne&#95; &#95;** macro peut être modifiée en utilisant un `#line` directive. Cette macro est toujours définie.

- **&#95;&#95;STDC&#95; &#95;**  défini en tant que 1 uniquement lorsque compilé en C et si le [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur est spécifiée. Sinon, non défini.

- **&#95;&#95;STDC&#95;hébergé&#95; &#95;**  la valeur 1 si l’implémentation est un *hébergé implémentation*, qui prend en charge la totalité de la bibliothèque standard requis. Sinon, elle est définie comme 0.

- **&#95;&#95;STDCPP&#95;THREADS&#95; &#95;**  la valeur 1 si et seulement si un programme peut avoir plusieurs threads d’exécution et compilé en C++. Sinon, non défini.

- **&#95;&#95;TEMPS&#95; &#95;**  l’heure de la traduction de l’unité de traduction prétraité. Le temps est une chaîne de caractères littérale du formulaire *hh : mm :*, identique à l’heure retournée par la bibliothèque CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md) (fonction). Cette macro est toujours définie.

## <a name="microsoft-specific-predefined-macros"></a>Macros prédéfinies spécifiques à Microsoft

MSVC prend en charge ces macros prédéfinies supplémentaires.

- **&#95;&#95;ATOM&#95; &#95;**  défini en tant que 1 lorsque le [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) option du compilateur est définie et la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95;&#95;AVX&#95; &#95;**  défini en tant que 1 lorsque le [/arch : AVX](../build/reference/arch-x86.md) ou [/arch : avx2](../build/reference/arch-x86.md) options du compilateur sont définies et la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95;&#95;AVX2&#95; &#95;**  défini en tant que 1 lorsque le [/arch : avx2](../build/reference/arch-x86.md) option du compilateur est définie et la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95;CHAR&#95;UNSIGNED** défini en tant que 1 si la valeur par défaut **char** type n’est pas signé. Cette valeur est définie lorsque le [/J (caractère par défaut est de Type non signé)](../build/reference/j-default-char-type-is-unsigned.md) option du compilateur est définie. Sinon, non défini.

- **&#95;&#95;CLR&#95;VER** défini comme un littéral d’entier qui représente la version du Common Language Runtime (CLR) utilisé pour compiler l’application. La valeur est encodée sous la forme `Mmmbbbbb`, où `M` est la version majeure du runtime, `mm` est la version secondaire du runtime, et `bbbbb` est le numéro de build. **&#95;&#95;CLR&#95;VER** est défini si le [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;CONTRÔLE&#95;flux&#95;protéger** défini en tant que 1 lorsque le [/Guard : CF (activer la protection de flux de contrôle)](../build/reference/guard-enable-control-flow-guard.md) option du compilateur est définie. Sinon, non défini.

- **&#95;&#95;COMPTEUR&#95; &#95;**  se développe pour un littéral d’entier commençant à 0. La valeur est incrémentée de 1 chaque fois qu’il a utilisé dans un fichier source, ou dans les en-têtes du fichier source inclus dans. **&#95;&#95;COMPTEUR&#95; &#95;**  conserve son état lorsque vous utilisez des en-têtes précompilés. Cette macro est toujours définie.

  Cet exemple utilise `__COUNTER__` pour affecter des identificateurs uniques aux trois objets différents du même type. Le `exampleClass` constructeur accepte un entier en tant que paramètre. Dans `main`, l’application déclare trois objets de type `exampleClass`, à l’aide `__COUNTER__` en tant que paramètre d’identificateur unique :

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

- **&#95;&#95;cplusplus&#95;cli** défini comme la valeur de littéral d’entier 200406 lors de la compilation en C++ et un [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini. Lorsque défini,  **&#95; &#95;cplusplus&#95;cli** est en vigueur tout au long de l’unité de traduction.

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

- **&#95;&#95;cplusplus&#95;winrt** défini comme la valeur de littéral d’entier 201009 lors de la compilation en C++ et le [/ZW (Compilation pour le Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;CPPRTTI** défini en tant que 1 si le [/GR (activer les informations de Type au moment de l’exécution)](../build/reference/gr-enable-run-time-type-information.md) option du compilateur est définie. Sinon, non défini.

- **&#95;CPPUNWIND** la valeur 1 si une ou plusieurs de la [/GX (activer la gestion des exceptions)](../build/reference/gx-enable-exception-handling.md), [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), ou [/EH (Exception Handling Model)](../build/reference/eh-exception-handling-model.md) options du compilateur sont définies. Sinon, non défini.

- **&#95;DÉBOGUER** défini en tant que 1 lorsque le [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/MDd](../build/reference/md-mt-ld-use-run-time-library.md), ou [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) option du compilateur est définie. Sinon, non défini.

- **&#95;DLL** défini en tant que 1 lorsque le [/MD](../build/reference/md-mt-ld-use-run-time-library.md) ou [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) option du compilateur (DLL multithread) est définie. Sinon, non défini.

- **&#95;&#95;FUNCDNAME&#95; &#95;**  défini comme un littéral de chaîne qui contient le [nom décoré](../build/reference/decorated-names.md) de la fonction englobante. La macro est définie uniquement au sein d’une fonction. Le **&#95; &#95;FUNCDNAME&#95; &#95;** macro n’est pas développée si vous utilisez le [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/P](../build/reference/p-preprocess-to-a-file.md) option du compilateur.

   Cet exemple utilise le `__FUNCDNAME__`, `__FUNCSIG__`, et `__FUNCTION__` macros pour afficher des informations sur la fonction.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95;&#95;FUNCSIG&#95; &#95;**  défini comme un littéral de chaîne qui contient la signature de la fonction englobante. La macro est définie uniquement au sein d’une fonction. Le **&#95; &#95;FUNCSIG&#95; &#95;** macro n’est pas développée si vous utilisez le [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/P](../build/reference/p-preprocess-to-a-file.md) option du compilateur. Lors de la compilation pour une cible 64 bits, la convention d’appel est `__cdecl` par défaut. Pour obtenir un exemple d’utilisation, consultez le `__FUNCDNAME__` macro.

- **&#95;&#95;FONCTION&#95; &#95;**  défini comme un littéral de chaîne qui contient le nom non décoré de la fonction englobante. La macro est définie uniquement au sein d’une fonction. Le **&#95; &#95;fonction&#95; &#95;** macro n’est pas développée si vous utilisez le [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/P](../build/reference/p-preprocess-to-a-file.md) option du compilateur. Pour obtenir un exemple d’utilisation, consultez le `__FUNCDNAME__` macro.

- **&#95;INTÉGRAUX&#95;MAX&#95;BITS** définis en tant que la valeur de littéral d’entier 64, la taille maximale (en bits) pour un type intégral non vectoriel. Cette macro est toujours définie.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95;&#95;INTELLISENSE&#95; &#95;**  défini comme étant 1 pendant un compilateur IntelliSense passer dans l’IDE Visual Studio. Sinon, non défini. Vous pouvez utiliser cette macro pour la protection du code du compilateur IntelliSense ne comprendre, ou l’utiliser pour basculer entre la génération et le compilateur IntelliSense. Pour plus d’informations, consultez [conseils de dépannage pour les lenteurs IntelliSense](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;VOLATILE** défini en tant que 1 si le [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;NOYAU&#95;MODE** défini en tant que 1 si le [/kernel (créer Kernel Mode binaire)](../build/reference/kernel-create-kernel-mode-binary.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;AMD64** défini comme étant le littéral entier valeur 100 pour les compilations qui x64 de cibler les processeurs. Sinon, non défini.

- **&#95;M&#95;ARM** défini comme la valeur de littéral d’entier 7 pour les compilations qui ciblent les processeurs ARM. Sinon, non défini.

- **&#95;M&#95;ARM&#95;ARMV7VE** défini en tant que 1 lorsque le [armv7ve](../build/reference/arch-arm.md) option du compilateur est définie pour les compilations qui ciblent les processeurs ARM. Sinon, non défini.

- **&#95;M&#95;ARM&#95;FP** défini en tant que valeur littérale entière qui indique quelle [/arch](../build/reference/arch-arm.md) option du compilateur a été définie pour les cibles de processeur ARM. Sinon, non défini.

  - Une valeur dans la plage 30-39, si aucune `/arch` ARM option a été spécifiée, indiquant l’architecture par défaut pour ARM a été défini (`VFPv3`).

  - Une valeur dans la plage 40-49 si `/arch:VFPv4` a été défini.

  - Pour plus d’informations, consultez [/arch (ARM)](../build/reference/arch-arm.md).

- **&#95;M&#95;ARM64** la valeur 1 pour les compilations qui ciblent des processeurs ARM de 64 bits. Sinon, non défini.

- **&#95;M&#95;CEE** défini comme 001 si de [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;CEE&#95;pur** déconseillée à compter de Visual Studio 2015. Macro définie comme 001 si le [/CLR : pure](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;CEE&#95;SAFE** déconseillée à compter de Visual Studio 2015. Macro définie comme 001 si le [/CLR : safe](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;EXCEPT** défini en tant que 1 si le [/fp : sauf](../build/reference/fp-specify-floating-point-behavior.md) ou [/fp : strict](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;rapide** défini en tant que 1 si le [Fast](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;PRECISE** défini en tant que 1 si le [/fp : precise](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;STRICT** défini en tant que 1 si le [/fp : strict](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;IX86** défini comme étant le littéral entier valeur 600 pour les compilations qui x86 de cibler les processeurs. Cette macro n’est pas définie pour x64 ou les cibles de compilation ARM.

- **&#95;M&#95;IX86&#95;FP** définie comme une valeur de littéral d’entier qui indique le [/arch](../build/reference/arch-arm.md) option du compilateur qui a été définie, ou la valeur par défaut. Cette macro est toujours définie lorsque la cible de compilation est un x86 processeur. Sinon, non défini. Lorsque défini, la valeur est :

  - 0 si le `/arch:IA32` option du compilateur a été définie.

  - 1 si la `/arch:SSE` option du compilateur a été définie.

  - 2 si la `/arch:SSE2`, `/arch:AVX`, ou `/arch:AVX2` option du compilateur a été définie. Cette valeur est la valeur par défaut si un `/arch` option du compilateur n’a pas été spécifiée. Lorsque `/arch:AVX` est spécifié, la macro **&#95; &#95;AVX&#95; &#95;** est également défini. Lorsque `/arch:AVX2` est spécifié, les deux **&#95; &#95;AVX&#95; &#95;** et **&#95; &#95;AVX2&#95; &#95;** sont également définies.

  - Pour plus d’informations, consultez l’article [/arch (x86)](../build/reference/arch-x86.md).

- **&#95;M&#95;X64** défini comme étant le littéral entier valeur 100 pour les compilations qui x64 de cibler les processeurs. Sinon, non défini.

- **&#95;MANAGED** défini en tant que 1 lorsque le [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;MSC&#95;BUILD** défini comme un littéral d’entier qui contient l’élément de numéro de révision du numéro de version du compilateur. Le numéro de révision est le quatrième élément du numéro de version délimité. Par exemple, si le numéro de version du compilateur Microsoft C/C++ est 15.00.20706.01, la  **&#95;MSC&#95;BUILD** macro prend la valeur 1. Cette macro est toujours définie.

- **&#95;MSC&#95;EXTENSIONS** défini en tant que 1 si l’activé par défaut [/Ze (activer les Extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) option du compilateur est définie. Sinon, non défini.

- **&#95;MSC&#95;complète&#95;VER** défini comme un littéral d’entier qui code majeure, mineure et générer le nombre d’éléments contenus du numéro de version du compilateur. Le numéro principal est le premier élément du numéro de version délimité, le numéro secondaire est le deuxième élément, et le numéro de build est le troisième élément. Par exemple, si le numéro de version du compilateur Microsoft C/C++ est 15.00.20706.01, la  **&#95;MSC&#95;complète&#95;VER** macro prend la valeur 150020706. Entrez `cl /?` sur la ligne de commande pour afficher le numéro de version du compilateur. Cette macro est toujours définie.

- **&#95;MSC&#95;VER** défini comme un littéral d’entier qui code les éléments de numéros majeurs et mineurs du numéro de version du compilateur. Le numéro principal est le premier élément du numéro de version délimité et le numéro secondaire est le deuxième élément. Par exemple, si le numéro de version du compilateur Microsoft C/C++ est 17.00.51106.1, la  **&#95;MSC&#95;VER** macro prend la valeur 1700. Entrez `cl /?` sur la ligne de commande pour afficher le numéro de version du compilateur. Cette macro est toujours définie.

   |Version de Visual Studio|**&#95;MSC&#95;VER**|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7.0)|1300|
   |Visual Studio .NET 2003 (7.1)|1310|
   |Visual Studio 2005 (8.0)|1400|
   |Visual Studio 2008 (9.0)|1500|
   |Visual Studio 2010 (10.0)|1600|
   |Visual Studio 2012 (11.0)|1700|
   |Visual Studio 2013 (12.0)|1800|
   |Visual Studio 2015 (14.0)|1900|
   |Visual Studio 2017 RTW (15.0)|1910|
   |Visual Studio 2017 version 15.3|1911|
   |Visual Studio 2017 version 15.5|1912|
   |Visual Studio 2017 version 15.6|1913|
   |Visual Studio 2017 version 15.7|1914|
   |Visual Studio 2017 version 15.8|1915|
   |Visual Studio 2017 version 15.9|1916|
   |Visual Studio 2019 RTW (16.0)|1920|

   Pour tester les versions du compilateur ou mises à jour dans une version donnée de Visual Studio, ou après, utilisez le **>=** opérateur. Vous pouvez l’utiliser dans une directive conditionnelle pour comparer  **&#95;MSC&#95;VER** par rapport à cette version connue. Si vous avez plusieurs versions mutuellement à comparer, commander des comparaisons dans l’ordre décroissant de numéro de version. Par exemple, ce code vérifie les compilateurs publiés dans Visual Studio 2017 et versions ultérieures. Ensuite, il recherche des compilateurs publiés dans ou après Visual Studio 2015. Puis il vérifie tous les compilateurs publiées avant Visual Studio 2015 :

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   Pour plus d’informations, consultez [Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) dans le Blog de l’équipe Microsoft C++.

- **&#95;MSVC&#95;LANG** défini comme un littéral d’entier qui spécifie la norme du langage C++ ciblée par le compilateur. Il est défini uniquement dans le code compilé en C++. La macro est le littéral entier L 201402 la valeur par défaut, ou lorsque le [/std : c ++ 14](../build/reference/std-specify-language-standard-version.md) option du compilateur est spécifiée. La macro est définie sur L 201703 si le [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md) option du compilateur est spécifiée. Il est défini sur une valeur plus élevée, non spécifiée lors de la [/std : c ++ dernière](../build/reference/std-specify-language-standard-version.md) option est spécifiée. Sinon, la macro n’est pas définie. Le  **&#95;MSVC&#95;LANG** macro et [/STD (Specify Language Standard Version)](../build/reference/std-specify-language-standard-version.md) options du compilateur sont disponible à compter de Visual Studio 2015 Update 3.

- **&#95;&#95;MSVC&#95;RUNTIME&#95;VÉRIFIE** la valeur 1 lorsque l’une de le [/RTC](../build/reference/rtc-run-time-error-checks.md) options du compilateur est définie. Sinon, non défini.

- **&#95;MT** défini en tant que 1 lorsque [/MD ou /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (DLL multithread) ou [/MT ou /MTd](../build/reference/md-mt-ld-use-run-time-library.md) (multithread) est spécifié. Sinon, non défini.

- **&#95;NATIF&#95;WCHAR&#95;T&#95;défini par** défini en tant que 1 lorsque le [/Zc : wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) option du compilateur est définie. Sinon, non défini.

- **&#95;OPENMP** défini en tant qu’entier 200203 littéral, si le [/openmp (activer OpenMP 2.0 prise en charge)](../build/reference/openmp-enable-openmp-2-0-support.md) option du compilateur est définie. Cette valeur représente la date de la spécification OpenMP implémentée par MSVC. Sinon, non défini.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST&#95;**  défini en tant que 1 lorsque le [/ analyze](../build/reference/analyze-code-analysis.md) option du compilateur est définie. Sinon, non défini.

- **&#95;&#95;HORODATAGE&#95; &#95;**  défini comme un littéral de chaîne qui contient la date et l’heure de la dernière modification du fichier source actuel, sous la forme abrégée, constante Longueur retournée par la bibliothèque CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md) fonction, par exemple, `Fri 19 Aug 13:32:58 2016`. Cette macro est toujours définie.

- **&#95;VC&#95;/NODEFAULTLIB** défini en tant que 1 lorsque le [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) option du compilateur est définie. Sinon, non défini.

- **&#95;WCHAR&#95;T&#95;défini par** défini en tant que 1 lorsque la valeur par défaut [/Zc : wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) option du compilateur est définie. Le  **&#95;WCHAR&#95;T&#95;défini par** macro est définie, mais elle n’a aucune valeur si le `/Zc:wchar_t-` option du compilateur est définie, et **wchar_t** est défini dans un fichier d’en-tête système inclus dans votre projet. Sinon, non défini.

- **&#95;Win32** définis en tant que 1 lorsque la cible de compilation est ARM 32 bits, 64 bits, ARM, x86, ou x 64. Sinon, non défini.

- **&#95;Win64** la valeur 1 lorsque la cible de compilation est 64 bits ARM ou x64. Sinon, non défini.

- **&#95;WINRT&#95;DLL** défini en tant que 1 lorsque compilé en C++ et les deux [/ZW (Compilation pour le Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) et [/LD ou /LDd](../build/reference/md-mt-ld-use-run-time-library.md) options du compilateur sont définies. Sinon, non défini.

Aucune macro de préprocesseur qui identifient la version de la bibliothèque ATL ou MFC n’est prédéfinies par le compilateur. ATL et des en-têtes de la bibliothèque MFC définissent ces macros de version en interne. Ils sont non définis dans les directives de préprocesseur effectuées avant que l’en-tête requis est inclus.

- **&#95;ATL&#95;VER** définies dans \<atldef.h > comme un littéral d’entier qui encode le numéro de version ATL.

- **&#95;MFC&#95;VER** définies dans \<afxver_.h > comme un littéral d’entier qui encode le numéro de version MFC.

## <a name="see-also"></a>Voir aussi

[Macros (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)<br/>
[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)