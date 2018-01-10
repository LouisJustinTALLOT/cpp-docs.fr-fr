---
title: -clr Restrictions | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa0bdc6a5a62b517c252a35d8f1193b34d6e0d32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="clr-restrictions"></a>Restrictions de /clr
Notez les restrictions suivantes sur l’utilisation de **/CLR**:  
  
-   Dans un gestionnaire d’exceptions structuré, il existe des restrictions sur l’utilisation de `_alloca` lors de la compilation avec **/CLR**. Pour plus d’informations, consultez [_alloca](../../c-runtime-library/reference/alloca.md).  
  
-   L’utilisation de vérifications des erreurs au moment de l’exécution n’est pas valide avec **/CLR**. Pour plus d’informations, consultez [Comment : utiliser les contrôles natifs à l'exécution](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
-   Lorsque **/CLR** est utilisé pour compiler un programme qui utilise uniquement la syntaxe C++ standard, les indications suivantes s’appliquent à l’utilisation de l’assembleur inline :  
  
    -   Code d’assembly inline qui suppose la connaissance de la disposition de la pile native, conventions en dehors de la fonction en cours ou d’autres informations de bas niveau sur l’ordinateur d’appel peuvent échouer si cette base de connaissances est appliquée au frame de pile pour une fonction managée. Les fonctions contenant du code assembleur inline sont générées en tant que fonctions non managées, comme si elles ont été placées dans un module distinct qui a été compilé sans **/CLR**.  
  
    -   Le code assembleur inline dans les fonctions qui passent des paramètres de fonction construits par copie n’est pas pris en charge.  
  
-   Le [fonctions vprintf](../../c-runtime-library/vprintf-functions.md) ne peut pas être appelée à partir d’un programme compilé avec **/CLR**.  
  
-   Le [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) modificateur est ignoré sous/CLR.  
  
-   La fonction définie par [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) uniquement sur les interceptions dans le code non managé. Consultez [la gestion des exceptions](../../windows/exception-handling-cpp-component-extensions.md) pour plus d’informations.  
  
-   La comparaison des pointeurs de fonction n’est pas autorisée sous **/CLR**.  
  
-   L’utilisation de fonctions qui ne sont pas entièrement prototypées n’est pas autorisée sous **/CLR**.  
  
-   Les options du compilateur suivantes ne sont pas pris en charge avec **/CLR**:  
  
    -   **/ /EHsc** et **/EHs** (**/CLR** implique **/EHa** (consultez [/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md))  
  
    -   **/ fp : strict** et **/fp : sauf** (consultez [/fp (spécifier du comportement de nombres à virgule flottante)](../../build/reference/fp-specify-floating-point-behavior.md))  
  
    -   [/ Zd](../../build/reference/z7-zi-zi-debug-information-format.md)  
  
    -   [/Gm](../../build/reference/gm-enable-minimal-rebuild.md)  
  
    -   [/MT](../../build/reference/md-mt-ld-use-run-time-library.md)  
  
    -   [/RTC](../../build/reference/rtc-run-time-error-checks.md)  
  
    -   **/ ZI**  
  
-   La combinaison de la `_STATIC_CPPLIB` définition du préprocesseur (`/D_STATIC_CPPLIB`) et le **/CLR** ou **/CLR : pure** option du compilateur n’est pas pris en charge. Ceci est le cas, car la définition provoquerait votre application lier avec la statique multithread bibliothèque Standard C++, ce qui n’est pas pris en charge. Pour plus d’informations, consultez la [/MD, / MT, /LD (utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md) rubrique.  
  
-   [/J](../../build/reference/j-default-char-type-is-unsigned.md) n’est pas pris en charge avec **/CLR : safe** ou **/CLR : pure**. Les options de compilateur **/clr:pure** et **/clr:safe** sont dépréciées dans Visual Studio 2015.  
  
-   Les bibliothèques ATL et MFC ne sont pas pris en charge par la compilation en mode pur (**/CLR : pure**). Vous pouvez utiliser **/CLR : pure** avec la bibliothèque C++ Standard et la bibliothèque CRT si vous compilez également avec **/MD** ou **/MDd**.  
  
-   Lorsque vous utilisez **/Zi** avec **/CLR**, il existe des conséquences sur les performances. Pour plus d’informations, consultez [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
-   La routine de sortie en passant un caractère large à .NET Framework sans spécifier également [/Zc :](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) ou sans casting du caractère en `__wchar_t` entraîne la sortie apparaisse comme un `unsigned short int`. Exemple :  
  
    ```  
    Console::WriteLine(L' ')              // Will output 32.  
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.  
    ```  
  
-   [/GS](../../build/reference/gs-buffer-security-check.md) est ignoré lors de la compilation avec **/CLR**, sauf si une fonction se trouve sous `#pragma` [non managé](../../preprocessor/managed-unmanaged.md) ou si la fonction doit être compilée en mode natif, auquel cas le compilateur générer l’avertissement C4793, qui est désactivée par défaut.  
  
-   Consultez [/ENTRY](../../build/reference/entry-entry-point-symbol.md) pour connaître les conditions de signature d’une application managée.  
  
-   Les applications compilées avec **/openmp** et **/CLR** peut uniquement être exécuté dans un processus appdomain unique.  Consultez [/openmp (activer OpenMP 2.0 prise en charge)](../../build/reference/openmp-enable-openmp-2-0-support.md) pour plus d’informations.  
  
-   Les fonctions qui acceptent un nombre variable d’arguments (varargs) seront générées en tant que fonctions natives. Les types de données managées à la position de l’argument de variable seront marshalés vers des types natifs. Notez que <xref:System.String?displayProperty=fullName> types sont des chaînes à caractères larges en réalité, mais ils sont marshalés vers des chaînes de caractères d’un octet. Par conséquent, si un spécificateur printf est %S (wchar_t *), il marshalera en une chaîne de %s à la place.  
  
-   Lorsque vous utilisez la macro va_arg, vous risquez d’obtenir des résultats inattendus lors de la compilation avec **/CLR : pure**.  Pour plus d’informations, consultez [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md).  
  
-   Si votre application passe un argument de type [va_list](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) à une fonction déclarée prendre un nombre variable d’arguments, et que votre application est compilée avec **/CLR : pure**, le CLR lève <xref:System.NotSupportedException>. Si **/CLR** est utilisé à la place, les fonctions affectées sont compilées en code natif et s’exécuter correctement. Si **/CLR : safe** est utilisé, une erreur de diagnostic est émise.  
  
-   Vous ne devez appeler, à partir du code managé, toutes les fonctions qui parcourt la pile pour obtenir des informations sur les paramètres (arguments de fonction) ; la couche P/Invoke repousse ces informations plus bas dans la pile.  Par exemple, ne compilez pas de proxy/stub avec **/CLR**.  
  
-   Fonctions seront compilées en code managé chaque fois que possible, mais pas toutes les constructions C++ peuvent être traduites en code managé.  Cette détermination est effectuée sur une base fonction par fonction. Si n’importe quelle partie d’une fonction ne peut pas être convertie en code managé, la fonction entière sera convertie en code natif à la place. Les cas suivants empêchent le compilateur de générer du code managé.  
  
    -   Conversions de code généré par le compilateur ou fonctions d’assistance. Conversions de code natives sont générées pour tout appel de fonction via un pointeur fonction, y compris les appels de fonction virtuelle.  
  
    -   Les fonctions qui appellent `setjmp` ou `longjmp`.  
  
    -   Fonctions qui utilisent certaines routines intrinsèques pour manipuler directement des ressources de l’ordinateur. Par exemple, l’utilisation de `__enable` et `__disable`, `_ReturnAddress` et `_AddressOfReturnAddress`, ou intrinsèques multimédias seront tous les résultats dans du code natif.  
  
    -   Fonctions qui suivent la `#pragma unmanaged` directive. (Notez que l’inverse, `#pragma managed`, est également pris en charge.)  
  
    -   Une fonction qui contient des références à des types alignés, autrement dit, les types déclarés à l’aide de `__declspec(align(...))`.  
  
-   Vous ne pouvez pas utiliser le [Support COM du compilateur](../../cpp/compiler-com-support.md) classes avec **/CLR : pure** ou **/CLR : safe**.  
  
## <a name="see-also"></a>Voir aussi  
 [/CLR (Compilation pour le common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)