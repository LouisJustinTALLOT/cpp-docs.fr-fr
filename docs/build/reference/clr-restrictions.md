---
title: Restrictions de /clr
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 21b7ead553871854c73021756eb2086f9e6e7393
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777816"
---
# <a name="clr-restrictions"></a>Restrictions de /clr

Notez les restrictions suivantes sur l’utilisation de **/CLR**:

- Dans un gestionnaire d’exceptions structurées, il existe des restrictions sur l’utilisation de `_alloca` lors de la compilation avec **/CLR**. Pour plus d’informations, consultez [_alloca](../../c-runtime-library/reference/alloca.md).

- L’utilisation de vérifications des erreurs au moment de l’exécution n’est pas valide avec **/CLR**. Pour plus d'informations, voir [Procédure : utiliser les vérifications natives à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Lorsque **/CLR** est utilisé pour compiler un programme qui utilise uniquement la syntaxe C++ standard, les instructions suivantes s’appliquent à l’utilisation de l’assembly inline :

  - Code assembleur inline qui suppose des connaissances de la disposition de pile native, conventions en dehors de la fonction active, ou autres informations de bas niveau sur l’ordinateur d’appel peuvent échouer si cette connaissance est appliquée au frame de pile pour une fonction managée. Les fonctions contenant le code assembleur inline sont générées en tant que fonctions non managées, comme si elles ont été placées dans un module distinct qui a été compilé sans **/CLR**.

  - Le code assembleur inline dans les fonctions qui passent des paramètres de la fonction construit par copie n’est pas pris en charge.

- Le [vprintf, fonctions](../../c-runtime-library/vprintf-functions.md) ne peut pas être appelée à partir d’un programme compilé avec **/CLR**.

- Le [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) modificateur est ignoré sous/CLR.

- La fonction de traduction défini par [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) uniquement sur les interceptions dans le code non managé. Consultez [gestion des exceptions](../../extensions/exception-handling-cpp-component-extensions.md) pour plus d’informations.

- La comparaison de pointeurs de fonction n’est pas autorisée sous **/CLR**.

- L’utilisation de fonctions qui ne sont pas entièrement prototypées n’est pas autorisée sous **/CLR**.

- Les options du compilateur suivantes ne sont pas pris en charge avec **/CLR**:

  - **/ EHsc** et **/EHs** (**/CLR** implique **/EHa** (consultez [/EH (modèle de gestion des exceptions)](eh-exception-handling-model.md))

  - **/ fp : strict** et **/fp : sauf** (consultez [/fp (spécifier le comportement de virgule flottante)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- La combinaison de la `_STATIC_CPPLIB` définition du préprocesseur (`/D_STATIC_CPPLIB`) et le **/CLR** option du compilateur n’est pas pris en charge. Cela est le cas, car la définition de plantage de l’application effectuer une liaison avec la statique multithread bibliothèque C++ Standard, qui n’est pas pris en charge. Pour plus d’informations, consultez le [/MD, / MT, /LD (utiliser la bibliothèque Runtime)](md-mt-ld-use-run-time-library.md) rubrique.

- Lorsque vous utilisez **/Zi** avec **/CLR**, impacte les performances. Pour plus d’informations, consultez [/Zi](z7-zi-zi-debug-information-format.md).

- La routine de sortie en passant un caractère large à un Framework .NET sans spécifier également [/Zc : wchar_t](zc-wchar-t-wchar-t-is-native-type.md) ou sans casting du caractère en `__wchar_t` entraîne la sortie d’apparaître comme un `unsigned short int`. Exemple :

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md) est ignoré lors de la compilation avec **/CLR**, sauf si une fonction est sous `#pragma` [non managé](../../preprocessor/managed-unmanaged.md) ou si la fonction doit être compilée en natif, auquel cas le compilateur génère avertissement C4793, qui est désactivée par défaut.

- Consultez [/Entry](entry-entry-point-symbol.md) pour les exigences de signature de fonction d’une application managée.

- Les applications compilées avec **/OpenMP** et **/CLR** peut uniquement être exécuté dans un processus appdomain unique.  Consultez [/openmp (activer OpenMP 2.0 prise en charge)](openmp-enable-openmp-2-0-support.md) pour plus d’informations.

- Fonctions qui acceptent un nombre variable d’arguments (varargs) seront générées en tant que fonctions natives. Les types de données managés dans la position d’argument variable seront marshalés vers des types natifs. Notez que <xref:System.String?displayProperty=fullName> types sont des chaînes à caractères larges en fait, mais ils sont marshalés vers des chaînes de caractères d’un octet. Par conséquent, si un spécificateur printf est %S (wchar_t *), il sera marshaler une chaîne de %s à la place.

- Lorsque vous utilisez la macro va_arg, vous pouvez obtenir des résultats inattendus lors de la compilation avec **/CLR : pure**. Pour plus d’informations, consultez [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Code qui doit être « pur » ou « sécurisée » doit être déplacée vers C#.

- N’appelez pas, à partir du code managé, toutes les fonctions qui parcourt la pile pour obtenir des informations sur les paramètres (arguments de fonction) ; la couche de P/Invoke, cette information de plus bas dans la pile.  Par exemple, ne compilez pas de proxy/stub avec **/CLR**.

- Fonctions est compilées en code managé chaque fois que possible, mais pas toutes les constructions C++ peuvent être traduites vers le code managé.  Cette détermination est faite sur une base fonction par fonction. Si n’importe quelle partie d’une fonction ne peut pas être convertie en code managé, la fonction entière sera convertie en code natif à la place. Les cas suivants empêchent le compilateur de générer du code managé.

  - Conversions de code généré par le compilateur ou fonctions d’assistance. Thunks natifs sont générés pour tout appel de fonction via un pointeur de fonction, y compris les appels de fonction virtuelle.

  - Les fonctions qui appellent `setjmp` ou `longjmp`.

  - Fonctions qui utilisent certaines routines intrinsèques pour manipuler directement des ressources de l’ordinateur. Par exemple, l’utilisation de `__enable` et `__disable`, `_ReturnAddress` et `_AddressOfReturnAddress`, ou intrinsèques multimédias seront tous les résultats dans du code natif.

  - Fonctions qui suivent la `#pragma unmanaged` directive. (Notez que l’inverse, `#pragma managed`, est également pris en charge.)

  - Une fonction qui contient des références à des types alignés, autrement dit, les types déclarés à l’aide de `__declspec(align(...))`.

## <a name="see-also"></a>Voir aussi

- [/clr (Compilation pour le Common Language Runtime)](clr-common-language-runtime-compilation.md)
