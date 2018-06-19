---
title: Macros prédéfinies | Documents Microsoft
ms.custom: update_every_version
ms.date: 04/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 692279d8c19f2a03dcd9388eb47a640dcb00658a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32425242"
---
# <a name="predefined-macros"></a>Macros prédéfinies

Le compilateur Visual C++ prédéfinit certaines macros de préprocesseur, selon la langue (C ou C++), la cible de compilation et les options de compilateur choisie.

Visual C++ prend en charge les macros de préprocesseur prédéfinies requises spécifiées par la norme ANSI/ISO C99 et la norme C ++ 14 ISO. L’implémentation prend également en charge plusieurs macros préprocesseur plus spécifiques à Microsoft. Certaines macros sont définies uniquement pour les environnements de build spécifique ou les options du compilateur. Sauf indication, les macros sont définies dans l’ensemble d’une unité de traduction comme si elles ont été spécifiées en tant que **/D** arguments de l’option du compilateur. Lorsque défini, les macros sont développées pour les valeurs spécifiées par le préprocesseur avant la compilation. Les macros prédéfinies ne prennent pas d’arguments et ne peut pas être redéfinis.

## <a name="standard-predefined-identifier"></a>Identificateur prédéfini standard

Le compilateur prend en charge cet identificateur prédéfini spécifié par la norme ISO C99 et ISO C ++ 11.

- **&#95;&#95;Func&#95; &#95;**  le nom non qualifié et sans ornement de la fonction englobante comme fonction-local `static const` tableau de `char`.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Macros prédéfinies standards

Le compilateur prend en charge ces macros prédéfinies spécifiées par l’ISO C99 et C ++ 17 normes ISO.

- **&#95;&#95;cplusplus** définie comme une valeur littérale entière lorsque l’unité de traduction est compilée en C++. Sinon, non défini.

- **&#95;&#95;DATE&#95; &#95;**  la date de la compilation du fichier source actuel. La date est une chaîne de longueur constante littérale du formulaire *Mmm jj aaaa*. Le nom du mois *Mmm* est le même que le nom de mois abrégé dans dates générées par la bibliothèque Runtime C [asctime](../c-runtime-library/reference/asctime-wasctime.md) (fonction). Le premier caractère de date *jj* est un espace si la valeur est inférieure à 10. Cette macro est toujours définie.

- **&#95;&#95;FICHIER&#95; &#95;**  le nom du fichier source actuel. **&#95;&#95;FICHIER&#95; &#95;**  se développe en un littéral de chaîne de caractères. Pour vous assurer que le chemin d’accès complet au fichier s’affiche, utilisez [/FC (complet chemin d’accès du fichier de Code Source dans les Diagnostics)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Cette macro est toujours définie.

- **&#95;&#95;LIGNE&#95; &#95;**  défini comme le numéro de ligne entière dans le fichier source actuel. La valeur de la **&#95; &#95;ligne&#95; &#95;** (macro) peut être modifié en utilisant un `#line` la directive. Cette macro est toujours définie.

- **&#95;&#95;STDC&#95; &#95;**  défini comme 1 uniquement lors de la compilation en C et si le [/Za](../build/reference/za-ze-disable-language-extensions.md) option du compilateur est spécifiée. Sinon, non défini.

- **&#95;&#95;STDC&#95;HOSTED&#95; &#95;**  défini comme 1, si l’implémentation est un *hébergé implémentation*, qui prend en charge l’intégralité de la bibliothèque standard requis. Sinon, elle est définie comme 0.

- **&#95;&#95;STDCPP&#95;THREADS&#95; &#95;**  définis sur 1 si et seulement si un programme peut avoir plusieurs threads d’exécution et compilé en C++. Sinon, non défini.

- **&#95;&#95;TEMPS&#95; &#95;**  l’heure de la traduction de l’unité de traduction prétraité. L’heure est une chaîne de caractères littérale du formulaire *hh : mm :*, identique à l’heure retournée par la bibliothèque Runtime C [asctime](../c-runtime-library/reference/asctime-wasctime.md) (fonction). Cette macro est toujours définie.

## <a name="microsoft-specific-predefined-macros"></a>Macros prédéfinies spécifiques à Microsoft

Microsoft Visual C++ prend en charge ces macros prédéfinies supplémentaires.

- **&#95;&#95;ATOM&#95; &#95;**  défini en tant que 1 lorsque la [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) option du compilateur est définie et la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95;&#95;AVX&#95; &#95;**  défini en tant que 1 lorsque la [/arch : AVX](../build/reference/arch-x86.md) ou [/arch : avx2](../build/reference/arch-x86.md) définir des options du compilateur et la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95;&#95;AVX2&#95; &#95;**  défini en tant que 1 lorsque la [/arch : avx2](../build/reference/arch-x86.md) option du compilateur est définie et la cible du compilateur est x86 ou x64. Sinon, non défini.

- **&#95;CHAR&#95;UNSIGNED** défini en tant que 1, si la valeur par défaut `char` type n’est pas signé. Cette option est définie lorsque le [/J (caractère par défaut est de Type non signé)](../build/reference/j-default-char-type-is-unsigned.md) option du compilateur est définie. Sinon, non défini.

- **&#95;&#95;CLR&#95;VER** définie comme un littéral d’entier qui représente la version du common language runtime utilisée lors de l’application a été compilée. La valeur est encodée sous la forme `Mmmbbbbb`, où `M` est la version principale du runtime, `mm` est la version mineure de l’exécution, et `bbbbb` est le numéro de build. **&#95;&#95;CLR&#95;VER** est défini si le [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;CONTRÔLE&#95;flux&#95;protection** défini en tant que 1 lorsque la [/Guard : CF (activer le contrôle de la protection du flux)](../build/reference/guard-enable-control-flow-guard.md) option du compilateur est définie. Sinon, non défini.

- **&#95;&#95;COMPTEUR&#95; &#95;**  se développe en un littéral d’entier qui commence à 0 et est incrémenté de 1 chaque fois qu’elle est utilisée dans un fichier source ou dans les en-têtes du fichier source inclus. **&#95;&#95;COMPTEUR&#95; &#95;**  conserve son état lorsque vous utilisez des en-têtes précompilés. Cette macro est toujours définie.

  Cet exemple utilise `__COUNTER__` pour affecter des identificateurs uniques à trois objets différents du même type. Le `exampleClass` constructeur accepte un entier en tant que paramètre. Dans `main`, l’application déclare trois objets de type `exampleClass`, à l’aide `__COUNTER__` en tant que paramètre d’identificateur unique :

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

- **&#95;&#95;cplusplus&#95;cli** définie comme la valeur de littéral d’entier 200406 lors de la compilation en C++ et un [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini. Lorsque défini,  **&#95; &#95;cplusplus&#95;cli** est en vigueur tout au long de l’unité de traduction.

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

- **&#95;&#95;cplusplus&#95;winrt** définie comme la valeur de littéral d’entier 201009 lors de la compilation en C++ et le [/ZW (Compilation Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;CPPRTTI** définie comme 1, si le [/GR (activer les informations de Type au moment de l’exécution)](../build/reference/gr-enable-run-time-type-information.md) option du compilateur est définie. Sinon, non défini.

- **&#95;CPPUNWIND** défini comme 1, si un ou plusieurs de la [/GX (activer la gestion des exceptions)](../build/reference/gx-enable-exception-handling.md), [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), ou [/EH (Exception Handling Model)](../build/reference/eh-exception-handling-model.md) options du compilateur sont définies. Sinon, non défini.

- **&#95;DÉBOGUER** défini en tant que 1 lorsque la [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/MDd](../build/reference/md-mt-ld-use-run-time-library.md), ou [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) option du compilateur est définie. Sinon, non défini.

- **&#95;DLL** défini en tant que 1 lorsque la [/MD](../build/reference/md-mt-ld-use-run-time-library.md) ou [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) option du compilateur (DLL multithread) est définie. Sinon, non défini.

- **&#95;&#95;FUNCDNAME&#95; &#95;**  définie comme un littéral de chaîne qui contient le [nom décoré](../build/reference/decorated-names.md) de la fonction englobante. La macro est définie uniquement dans une fonction. Le **&#95; &#95;FUNCDNAME&#95; &#95;** macro n’est pas développée si vous utilisez la [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/P](../build/reference/p-preprocess-to-a-file.md) option du compilateur.

   Cet exemple utilise le `__FUNCDNAME__`, `__FUNCSIG__`, et `__FUNCTION__` macros pour afficher des informations sur la fonction.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95;&#95;FUNCSIG&#95; &#95;**  définie comme un littéral de chaîne qui contient la signature de la fonction englobante. La macro est définie uniquement dans une fonction. Le **&#95; &#95;FUNCSIG&#95; &#95;** macro n’est pas développée si vous utilisez la [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/P](../build/reference/p-preprocess-to-a-file.md) option du compilateur. Lors de la compilation pour une cible 64 bits, la convention d’appel est `__cdecl` par défaut. Pour obtenir un exemple d’utilisation, consultez le `__FUNCDNAME__` (macro).

- **&#95;&#95;FONCTION&#95; &#95;**  définie comme un littéral de chaîne qui contient le nom non décoré de la fonction englobante. La macro est définie uniquement dans une fonction. Le **&#95; &#95;fonction&#95; &#95;** macro n’est pas développée si vous utilisez la [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) ou [/P](../build/reference/p-preprocess-to-a-file.md) option du compilateur. Pour obtenir un exemple d’utilisation, consultez le `__FUNCDNAME__` (macro).

- **&#95;INTÉGRAUX&#95;MAX&#95;BITS** défini en tant que la valeur de littéral d’entier 64, la taille maximale (en octets) d’un type intégral non vectoriel. Cette macro est toujours définie.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95;&#95;INTELLISENSE&#95; &#95;**  défini comme étant 1 pendant un compilateur IntelliSense passer dans l’IDE de Visual Studio. Sinon, non défini. Vous pouvez utiliser cette macro à la protection du code, le compilateur IntelliSense ne pas comprendre ou l’utiliser pour basculer entre la génération et du compilateur d’IntelliSense. Pour plus d’informations, consultez [conseils de dépannage pour IntelliSense lenteur](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;VOLATILE** définie comme 1, si le [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;NOYAU&#95;MODE** définie comme 1, si le [/kernel (créer Kernel Mode binaire)](../build/reference/kernel-create-kernel-mode-binary.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;AMD64** défini comme étant le littéral d’entier valeur 100 pour les compilations qui x64 de cibler les processeurs. Sinon, non défini.

- **&#95;M&#95;ARM** définie comme la valeur de littéral d’entier 7 pour les compilations qui ciblent des processeurs ARM. Sinon, non défini.

- **&#95;M&#95;ARM&#95;ARMV7VE** défini en tant que 1 lorsque la [armv7ve](../build/reference/arch-arm.md) option du compilateur est définie pour les compilations qui ciblent des processeurs ARM. Sinon, non défini.

- **&#95;M&#95;ARM&#95;FP** définie comme une valeur littérale entière indiquant les [/arch](../build/reference/arch-arm.md) option du compilateur a été définie, si la cible de compilation est un processeur ARM. Sinon, non défini.

  - Dans la plage 30-39, si aucune **/arch** ARM a été spécifiée, indiquant l’architecture par défaut pour ARM a été défini (`VFPv3`).

  - Dans la plage 40-49 si **vfpv4** a été défini.

  - Consultez [/arch (ARM)](../build/reference/arch-arm.md) pour plus d’informations.

- **&#95;M&#95;ARM64** défini comme 1 pour les compilations qui ciblent des processeurs ARM de 64 bits. Sinon, non défini.

- **&#95;M&#95;CEE** défini comme 001 si les [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;CEE&#95;PURE** déconseillée à compter de Visual Studio 2015. Macro définie comme 001 si le [/CLR : pure](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;CEE&#95;SAFE** déconseillée à compter de Visual Studio 2015. Macro définie comme 001 si le [/CLR : safe](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;EXCEPT** définie comme 1, si le [/fp : sauf](../build/reference/fp-specify-floating-point-behavior.md) ou [/fp : strict](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;rapide** définie comme 1, si le [Fast](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;PRECISE** définie comme 1, si le [/fp : précise](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;FP&#95;STRICT** définie comme 1, si le [/fp : strict](../build/reference/fp-specify-floating-point-behavior.md) option du compilateur est définie. Sinon, non défini.

- **&#95;M&#95;IX86** défini comme étant le littéral d’entier valeur 600 pour les compilations qui x86 de cibler les processeurs. Cette macro n’est pas définie pour x64 ou cibles de compilation ARM.

- **&#95;M&#95;IX86&#95;FP** définie comme une valeur littérale entière indiquant le [/arch](../build/reference/arch-arm.md) option du compilateur qui a été définie, ou la valeur par défaut. Cette macro est toujours définie lorsque la cible de compilation est x86 processeur. Sinon, non défini. Lorsque défini, la valeur est :

  - 0 si le **/arch:IA32** option du compilateur a été définie.

  - 1 si le **/arch : SSE** option du compilateur a été définie.

  - 2 si le **SSE2**, **/arch : AVX** ou **/arch : avx2** option du compilateur a été définie. Cette valeur est la valeur par défaut si un **/arch** option du compilateur n’a pas été spécifiée. Lorsque **/arch : AVX** est spécifié, la macro **&#95; &#95;AVX&#95; &#95;** est également défini. Lorsque **/arch : avx2** est spécifié, les deux **&#95; &#95;AVX&#95; &#95;** et **&#95; &#95;AVX2&#95; &#95;** sont également défini.

  - Consultez [/arch (x86)](../build/reference/arch-x86.md) pour plus d’informations.

- **&#95;M&#95;X64** défini comme étant le littéral d’entier valeur 100 pour les compilations qui x64 de cibler les processeurs. Sinon, non défini.

- **&#95;GÉRÉS** défini en tant que 1 lorsque la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur est définie. Sinon, non défini.

- **&#95;MSC&#95;générer** définie comme un littéral d’entier qui contient l’élément de numéro de révision du numéro de version du compilateur. Le numéro de révision est le quatrième élément du numéro de version de délimité. Par exemple, si le numéro de version du compilateur Visual C++ est 15.00.20706.01, la  **&#95;MSC&#95;générer** macro prend la valeur 1. Cette macro est toujours définie.

- **&#95;MSC&#95;EXTENSIONS** définie comme 1, si le [/Ze (activer les Extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) option du compilateur est définie, qui est la valeur par défaut. Sinon, non défini.

- **&#95;MSC&#95;complète&#95;VER** définie comme un littéral d’entier qui encode le numéro principal, secondaire et générer le nombre d’éléments contenus du numéro de version du compilateur. Le numéro principal est le premier élément du numéro de version de délimité, le numéro secondaire est le deuxième élément, et le numéro de build est le troisième élément. Par exemple, si le numéro de version du compilateur Visual C++ est 15.00.20706.01, la  **&#95;MSC&#95;complète&#95;VER** macro prend la valeur 150020706. Entrez **cl / ?** sur la ligne de commande pour afficher le numéro de version du compilateur. Cette macro est toujours définie.

- **&#95;MSC&#95;VER** définie comme un littéral d’entier qui code les éléments numéros majeures et mineures du numéro de version du compilateur. Le numéro principal est le premier élément du numéro de version de délimité et le numéro secondaire est le deuxième élément. Par exemple, si le numéro de version du compilateur Visual C++ est 17.00.51106.1, la  **&#95;MSC&#95;VER** macro prend la valeur 1700. Entrez **cl / ?** sur la ligne de commande pour afficher le numéro de version du compilateur. Cette macro est toujours définie.

   |Version de Visual Studio|&AMP;#95;MSC&AMP;#95;VER|
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
   |Visual Studio de 2017 RTW (15.0)|1910|
   |Visual Studio 2017 version 15.3|1911|
   |Visual Studio 2017 version 15.5|1912|
   |Visual Studio 2017 version 15.6|1913|
   |Visual Studio 2017 version 15.7|1914|

   Pour tester les versions du compilateur ou dans une version donnée de Visual Studio ou après les mises à jour, utilisez la **>=** (opérateur) (supérieur ou égal) pour comparer  **&#95;MSC&#95;VER** contre connu Version. Si vous avez plusieurs versions à comparer de manière s’excluent mutuellement, nous vous recommandons de que vous commandez des comparaisons en ordre décroissant de numéro de version. Par exemple, ce code vérifie les compilateurs publiés dans Visual Studio 2015 et versions ultérieures, puis compilateurs publiés dans ou après Visual Studio 2013, puis exécute une action pour tous les compilateurs publiés avant Visual Studio 2013 :

   ```cpp
   #if _MSC_VER >= 1900
   // . . .
   #elif _MSC_VER >= 1800
   // . . .
   #else
   // . . .
   #endif
   ```

   Pour plus d’informations, consultez [Visual C++ de Version du compilateur](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/) dans le Blog d’équipe Visual C++.

- **&#95;MSVC&#95;LANG** définie comme un littéral d’entier qui spécifie la norme du langage C++ ciblée par le compilateur. Lors de la compilation en C++, la macro est la valeur de littéral d’entier L 201402 si le [/std : c ++ 14](../build/reference/std-specify-language-standard-version.md) option du compilateur est définie, ou par défaut ; il a la valeur L 201703 si le [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md) option du compilateur est définie ; et il est défini sur un plus élevé, non spécifié en valeur lorsque le [/std : c ++ dernière](../build/reference/std-specify-language-standard-version.md). Dans le cas contraire, la macro n’est pas définie. Le  **&#95;MSVC&#95;LANG** macro et [/std (spécifier la Version Standard traduite)](../build/reference/std-specify-language-standard-version.md) options du compilateur sont disponibles à partir de Visual Studio 2015 Update 3.

- **&#95;&#95;MSVC&#95;RUNTIME&#95;VÉRIFIE** défini comme 1 lorsque l’une de le [/RTC](../build/reference/rtc-run-time-error-checks.md) options du compilateur est définie. Sinon, non défini.

- **&#95;MT** défini en tant que 1 lorsque [/MD ou /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (DLL multithread) ou [/MT ou /MTd](../build/reference/md-mt-ld-use-run-time-library.md) (multithread) est spécifié. Sinon, non défini.

- **&#95;NATIVE&#95;WCHAR&#95;T&#95;défini** défini en tant que 1 lorsque la [/Zc :](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) option du compilateur est définie. Sinon, non défini.

- **&#95;OPENMP** entier littéral 200203, représentant la date de la spécification OpenMP implémentée par Visual C++, si le [/openmp (activer OpenMP 2.0 prise en charge)](../build/reference/openmp-enable-openmp-2-0-support.md) option du compilateur est définie. Sinon, non défini.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST&#95;**  défini en tant que 1 lorsque la [/ analyze](../build/reference/analyze-code-analysis.md) option du compilateur est définie. Sinon, non défini.

- **&#95;&#95;HORODATAGE&#95; &#95;**  définie comme un littéral de chaîne qui contient la date et l’heure de la dernière modification du fichier source en cours, sous la forme abrégée de longueur constante retourné par la bibliothèque Runtime C [asctime](../c-runtime-library/reference/asctime-wasctime.md) de fonction, par exemple, `Fri 19 Aug 13:32:58 2016`. Cette macro est toujours définie.

- **&#95;VC&#95;/NODEFAULTLIB** défini en tant que 1 lorsque la [/Zl (omettre les nom de bibliothèque par défaut)](../build/reference/zl-omit-default-library-name.md) option du compilateur est définie. Sinon, non défini.

- **&#95;WCHAR&#95;T&#95;défini** défini en tant que 1 lorsque la valeur par défaut [/Zc :](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) option du compilateur est définie. Le  **&#95;WCHAR&#95;T&#95;défini** macro est défini, mais elle n’a aucune valeur si le **/Zc:wchar_t-** option du compilateur est définie, et `wchar_t` est défini dans un fichier d’en-tête système inclus dans votre projet. Sinon, non défini.

- **&#95;Win32** défini en tant que 1 lorsque la cible de compilation est ARM 32 bits, 64 bits, ARM, x86, ou x 64. Sinon, non défini.

- **&#95;Win64** défini comme 1 lorsque la cible de compilation est 64 bits ARM ou x64. Sinon, non défini.

- **&#95;WINRT&#95;DLL** défini en tant que 1 lorsque compilé en C++ et les deux [/ZW (Compilation Windows Runtime)](../build/reference/zw-windows-runtime-compilation.md) et [/LD ou /LDd](../build/reference/md-mt-ld-use-run-time-library.md) options du compilateur sont définies. Sinon, non défini.

 Macros de préprocesseur permet de déterminer la version de la bibliothèque ATL ou MFC ne sont pas prédéfinies par le compilateur. Ces macros sont définies dans les en-têtes de la bibliothèque, ils ne sont pas définies dans les directives de préprocesseur avant l’en-tête nécessaire est inclus.

- **&#95;ATL&#95;VER** définies dans \<atldef.h > comme un littéral d’entier qui encode le numéro de version ATL.

- **&#95;MFC&#95;VER** définies dans \<afxver_.h > comme un littéral d’entier qui encode le numéro de version MFC.

## <a name="see-also"></a>Voir aussi

[Macros (C/C++)](../preprocessor/macros-c-cpp.md)   
[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)   
[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
