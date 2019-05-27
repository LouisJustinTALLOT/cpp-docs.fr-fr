---
title: Restrictions de /clr
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: d0318ce2e23f92600d5a78d6472646ec91492152
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837373"
---
# <a name="clr-restrictions"></a>Restrictions de /clr

Notez les restrictions suivantes sur l’utilisation de **/clr** :

- Dans un gestionnaire d’exceptions structurées, il existe des restrictions sur l’utilisation de `_alloca` lors de la compilation avec **/clr**. Pour plus d’informations, consultez [_alloca](../../c-runtime-library/reference/alloca.md).

- L’utilisation de vérifications des erreurs au moment de l’exécution n’est pas valide avec **/clr**. Pour plus d'informations, voir [Procédure : utiliser les vérifications natives à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Lorsque **/clr** est utilisé pour compiler un programme qui utilise uniquement une syntaxe C++ standard, les instructions suivantes s’appliquent à l’utilisation de l’assembly inline :

  - Le code de l’assembly inline qui suppose des connaissances de la disposition de pile native, des conventions d’appel en dehors de la fonction active ou d’autres informations de bas niveau sur l’ordinateur peut échouer si ces connaissances sont appliquées au frame de pile pour une fonction managée. Les fonctions contenant le code de l’assembly inline sont générées en tant que fonctions non managées, comme si elles étaient placées dans un module distinct qui a été compilé sans **/clr**.

  - Le code de l’assembly inline dans les fonctions qui passent des paramètres de fonction construits par copie n’est pas pris en charge.

- Les [fonctions vprintf](../../c-runtime-library/vprintf-functions.md) ne peuvent pas être appelées à partir d’un programme compilé avec **/clr**.

- Le modificateur [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) est ignoré sous /clr.

- La fonction de traduction définie par [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) affecte uniquement les interceptions dans le code non managé. Pour plus d’informations, consultez [Gestion des exceptions](../../extensions/exception-handling-cpp-component-extensions.md).

- La comparaison de pointeurs de fonction n’est pas autorisée sous **/clr**.

- L’utilisation de fonctions qui ne sont pas entièrement prototypées n’est pas autorisée sous **/clr**.

- Les options du compilateur suivantes ne sont pas prises en charge avec **/clr** :

  - **/EHsc** et **/EHs** ( **/clr** implique **/EHa** (consultez [/EH (Modèle de gestion des exceptions)](eh-exception-handling-model.md))

  - **/fp:strict** et **/fp:except** (consultez [/fp (Spécifier le comportement de virgule flottante)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- La combinaison de la définition du préprocesseur `_STATIC_CPPLIB` (`/D_STATIC_CPPLIB`) et de l’option du compilateur **/clr** n’est pas prise en charge. Cela est dû au fait que la définition entraîne la liaison de l’application avec la bibliothèque standard C++ multithread statique, qui n’est pas prise en charge. Pour plus d’informations, consultez la rubrique [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](md-mt-ld-use-run-time-library.md).

- L’utilisation de **/Zi** avec **/clr** a des effets sur les performances. Pour plus d’informations, consultez [/Zi](z7-zi-zi-debug-information-format.md).

- La transmission d’un caractère large à une routine de sortie .NET Framework sans spécifier également [/Zc:wchar_t](zc-wchar-t-wchar-t-is-native-type.md) ou sans caster le caractère en `__wchar_t` entraîne l’affichage de la sortie comme `unsigned short int`. Par exemple :

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md) est ignoré lors de la compilation avec **/clr**, sauf si une fonction se trouve sous `#pragma` [non managé](../../preprocessor/managed-unmanaged.md) ou si la fonction doit être compilée en code natif, auquel cas le compilateur génère l’avertissement C4793, qui est désactivé par défaut.

- Consultez [/ENTRY](entry-entry-point-symbol.md) pour connaître les exigences de signature de fonction d’une application managée.

- Les applications compilées avec **/openmp** et **/clr** peuvent uniquement être exécutées dans un processus appdomain unique.  Pour plus d’informations, consultez [/openmp (Activer la prise en charge OpenMP 2.0)](openmp-enable-openmp-2-0-support.md).

- Les fonctions qui prennent un nombre variable d’arguments (varargs) seront générées en tant que fonctions natives. Les types de données managés dans la position d’argument de variable seront marshalés en types natifs. Notez que les types <xref:System.String?displayProperty=fullName> sont en fait des chaînes à caractères larges, mais ils sont marshalés en chaînes de caractères codés sur un octet. Par conséquent, si un spécificateur printf est %S (wchar_t*), il sera marshalé en une chaîne %s à la place.

- Lorsque vous utilisez la macro va_arg, vous pouvez obtenir des résultats inattendus lors de la compilation avec **/clr:pure**. Pour plus d’informations, consultez [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). Les options de compilateur **/clr:pure** et **/clr:safe** sont dépréciées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017 et ultérieur. Le code qui doit être « pur » ou « sécurisé » doit être déplacé vers C#.

- Vous ne devez pas appeler, à partir du code managé, des fonctions qui remontent la pile pour obtenir des informations sur les paramètres (arguments de fonction) ; la couche P/Invoke entraîne le placement de ces informations plus bas dans la pile.  Par exemple, ne compilez pas de proxy/stub avec **/clr**.

- Les fonctions seront compilées en code managé chaque fois que possible, mais les constructions C++ ne peuvent pas toutes être traduites en code managé.  Cette détermination est effectuée fonction par fonction. Si une partie d’une fonction ne peut pas être convertie en code managé, la fonction entière sera convertie en code natif à la place. Les cas suivants empêchent le compilateur de générer du code managé.

  - Fonctions d’assistance ou conversions de code (thunks) générées par le compilateur. Des thunks natifs sont générés pour tout appel de fonction via un pointeur de fonction, notamment les appels de fonction virtuels.

  - Fonctions qui appellent `setjmp` ou `longjmp`.

  - Fonctions qui utilisent certaines routines intrinsèques pour manipuler directement des ressources de l’ordinateur. Par exemple, l’utilisation de `__enable` et `__disable`, `_ReturnAddress` et `_AddressOfReturnAddress`, ou des intrinsèques multimédias aboutissent tous à du code natif.

  - Fonctions qui suivent la directive `#pragma unmanaged`. (Notez que l’inverse, `#pragma managed`, est également pris en charge.)

  - Fonction qui contient des références à des types alignés, autrement dit des types déclarés à l’aide de `__declspec(align(...))`.

## <a name="see-also"></a>Voir aussi

- [/clr (Compilation pour le Common Language Runtime)](clr-common-language-runtime-compilation.md)
