---
title: Mots clés (C++)
description: Répertorie les mots clés du langage C++ standard, les mots clés spécifiques à Microsoft et les mots clés spécifiques au contexte.
ms.custom: index-page
ms.date: 07/25/2020
helpviewer_keywords:
- keywords [C++]
ms.assetid: d7ca94a8-f785-41ce-9f73-d3c4fd508489
ms.openlocfilehash: eaf06522a6d48caeeb84ddefb0e2e172f0af419c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213370"
---
# <a name="keywords-c"></a>Mots clés (C++)

Les mots clés sont des identificateurs réservés prédéfinis qui ont des significations particulières. Ils ne peuvent pas être utilisés comme identificateurs dans votre programme. Les mots clés suivants sont réservés pour Microsoft C++. Les noms avec des traits de soulignement et des noms de début spécifiés pour C++/CX et C++/CLI sont des extensions Microsoft.

## <a name="standard-c-keywords"></a>Mots clés C++ standard

:::row:::
    :::column:::
        [`alignas`](align-cpp.md)<br/>
        [`alignof`](alignof-operator.md)<br/>
        [`and`](bitwise-and-operator-amp.md)<sup>b</sup><br/>
        [`and_eq`](assignment-operators.md)<sup>b</sup><br/>
        [`asm`](../assembler/inline/asm.md)<sup>un</sup><br/>
        [`auto`](auto-keyword.md)<br/>
        [`bitand`](bitwise-and-operator-amp.md)<sup>b</sup><br/>
        [`bitor`](bitwise-inclusive-or-operator-pipe.md)<sup>b</sup><br/>
        [`bool`](bool-cpp.md)<br/>
        [`break`](break-statement-cpp.md)<br/>
        [`case`](switch-statement-cpp.md)<br/>
        [`catch`](try-throw-and-catch-statements-cpp.md)<br/>
        [`char`](fundamental-types-cpp.md)<br/>
        [`char8_t`](fundamental-types-cpp.md)<sup>c</sup><br/>
        [`char16_t`](char-wchar-t-char16-t-char32-t.md)<br/>
        [`char32_t`](char-wchar-t-char16-t-char32-t.md)<br/>
        [`class`](class-cpp.md)<br/>
        [`compl`](one-s-complement-operator-tilde.md)<sup>b</sup><br/>
        **`concept`**<sup>c</sup><br/>
        [`const`](const-cpp.md)<br/>
        [`const_cast`](const-cast-operator.md)<br/>
        **`consteval`**<sup>c</sup><br/>
        [`constexpr`](constexpr-cpp.md)<br/>
    :::column-end:::
    :::column:::
        **`constinit`**<sup>c</sup><br/>
        [`continue`](continue-statement-cpp.md)<br/>
        **`co_await`**<sup>c</sup><br/>
        **`co_return`**<sup>c</sup><br/>
        **`co_yield`**<sup>c</sup><br/>
        [`decltype`](decltype-cpp.md)<br/>
        [`default`](switch-statement-cpp.md)<br/>
        [`delete`](delete-operator-cpp.md)<br/>
        [`do`](do-while-statement-cpp.md)<br/>
        [`double`](fundamental-types-cpp.md)<br/>
        [`dynamic_cast`](dynamic-cast-operator.md)<br/>
        [`else`](if-else-statement-cpp.md)<br/>
        [`enum`](enumerations-cpp.md)<br/>
        [`explicit`](user-defined-type-conversions-cpp.md)<br/>
        **`export`**<sup>c</sup><br/>
        [`extern`](using-extern-to-specify-linkage.md)<br/>
        [`false`](false-cpp.md)<br/>
        [`float`](fundamental-types-cpp.md)<br/>
        [`for`](for-statement-cpp.md)<br/>
        [`friend`](friend-cpp.md)<br/>
        [`goto`](goto-statement-cpp.md)<br/>
        [`if`](if-else-statement-cpp.md)<br/>
        [`inline`](inline-functions-cpp.md)<br/>
    :::column-end:::
    :::column:::
        [`int`](fundamental-types-cpp.md)<br/>
        [`long`](fundamental-types-cpp.md)<br/>
        [`mutable`](mutable-data-members-cpp.md)<br/>
        [`namespace`](namespaces-cpp.md)<br/>
        [`new`](new-operator-cpp.md)<br/>
        [`noexcept`](noexcept-cpp.md)<br/>
        [`not`](logical-negation-operator-exclpt.md)<sup>b</sup><br/>
        [`not_eq`](equality-operators-equal-equal-and-exclpt-equal.md)<sup>b</sup><br/>
        [`nullptr`](nullptr.md)<br/>
        [`operator`](operator-overloading.md)<br/>
        [`or`](logical-or-operator-pipe-pipe.md)<sup>b</sup><br/>
        [`or_eq`](assignment-operators.md)<sup>b</sup><br/>
        [`private`](private-cpp.md)<br/>
        [`protected`](protected-cpp.md)<br/>
        [`public`](public-cpp.md)<br/>
        [`register`](storage-classes-cpp.md#register) [`reinterpret_cast`](reinterpret-cast-operator.md)<br/>
        **`requires`**<sup>c</sup><br/>
        [`return`](return-statement-cpp.md)<br/>
        [`short`](fundamental-types-cpp.md)<br/>
        [`signed`](fundamental-types-cpp.md)<br/>
        [`sizeof`](sizeof-operator.md)<br/>
        [`static`](storage-classes-cpp.md)<br/>
        [`static_assert`](static-assert.md)<br/>
    :::column-end:::
    :::column:::
        [`static_cast`](static-cast-operator.md)<br/>
        [`struct`](struct-cpp.md)<br/>
        [`switch`](switch-statement-cpp.md)<br/>
        [`template`](templates-cpp.md)<br/>
        [`this`](this-pointer.md)<br/>
        [`thread_local`](storage-classes-cpp.md#thread_local)<br/>
        [`throw`](try-throw-and-catch-statements-cpp.md)<br/>
        [`true`](true-cpp.md)<br/>
        [`try`](try-throw-and-catch-statements-cpp.md)<br/>
        [`typedef`](aliases-and-typedefs-cpp.md)<br/>
        [`typeid`](typeid-operator.md)<br/>
        [`typename`](typename.md)<br/>
        [`union`](unions.md)<br/>
        [`unsigned`](fundamental-types-cpp.md)<br/>
        [`using`](using-declaration.md)déclaré<br/>
        [`using`](namespaces-cpp.md#using_directives)la<br/>
        [`virtual`](virtual-cpp.md)<br/>
        [`void`](void-cpp.md)<br/>
        [`volatile`](volatile-cpp.md)<br/>
        [`wchar_t`](fundamental-types-cpp.md)<br/>
        [`while`](while-statement-cpp.md)<br/>
        [`xor`](bitwise-exclusive-or-operator-hat.md)<sup>b</sup><br/>
        [`xor_eq`](assignment-operators.md)<sup>b</sup><br/>
    :::column-end:::
:::row-end:::

<sup>un</sup> mot clé spécifique à Microsoft **`__asm`** remplace la **`asm`** syntaxe C++. **`asm`** est réservé à la compatibilité avec d’autres implémentations C++, mais n’est pas implémenté. Utilisez **`__asm`** pour l’assembly inline sur les cibles x86. Microsoft C++ ne prend pas en charge l’assembly inline pour d’autres cibles.

<sup>b</sup> les synonymes de l’opérateur étendu sont des mots clés lorsque [`/permissive-`](../build/reference/permissive-standards-conformance.md) ou [ `/Za` \( désactivent les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié. Ils ne sont pas des mots clés lorsque les extensions Microsoft sont activées.

<sup>c</sup> pris en charge lorsque [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) est spécifié.

## <a name="microsoft-specific-c-keywords"></a>Mots clés C++ spécifiques à Microsoft

En C++, les identificateurs qui contiennent deux traits de soulignement consécutifs sont réservés aux implémentations du compilateur. La Convention Microsoft consiste à précéder les mots clés spécifiques à Microsoft de doubles traits de soulignement. Ces mots ne peuvent pas être utilisés en tant que noms d’identificateurs.

Les extensions Microsoft sont activées par défaut. Pour vous assurer que vos programmes sont entièrement portables, vous pouvez désactiver les extensions Microsoft en spécifiant l' [`/permissive-`](../build/reference/permissive-standards-conformance.md) option ou [ `/Za` \( Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) pendant la compilation. Ces options désactivent certains mots clés spécifiques à Microsoft.

Lorsque les extensions Microsoft sont activées, vous pouvez utiliser les mots clés Microsoft spécifiques dans vos programmes. Pour la compatibilité ANSI, ces mots clés sont précédés d'un trait de soulignement double. Pour la compatibilité descendante, les versions à un seul trait de soulignement d’un grand nombre de mots clés à deux traits de soulignement sont prises en charge. Le **`__cdecl`** mot clé est disponible sans trait de soulignement de début.

Le **`__asm`** mot clé remplace la **`asm`** syntaxe C++. **`asm`** est réservé à la compatibilité avec d’autres implémentations C++, mais n’est pas implémenté. Utilisez **`__asm`**.

Le **`__based`** mot clé a des utilisations limitées pour les compilations cibles 32 bits et 64 bits.

:::row:::
    :::column:::
        [`__alignof`](alignof-operator.md)<sup>e</sup><br/>
        [`__asm`](../assembler/inline/asm.md)<sup>e</sup><br/>
        [`__assume`](../intrinsics/assume.md)<sup>e</sup><br/>
        [`__based`](based-pointers-cpp.md)<sup>e</sup><br/>
        [`__cdecl`](cdecl.md)<sup>e</sup><br/>
        [`__declspec`](declspec.md)<sup>e</sup><br/>
        [`__event`](event.md)<br/>
        [`__except`](try-except-statement.md)<sup>e</sup><br/>
        [`__fastcall`](fastcall.md)<sup>e</sup><br/>
        [`__finally`](try-finally-statement.md)<sup>e</sup><br/>
        [`__forceinline`](inline-functions-cpp.md)<sup>e</sup><br/>
    :::column-end:::
    :::column:::
        [`__hook`](hook.md)<sup>d</sup><br/>
        [`__if_exists`](if-exists-statement.md)<br/>
        [`__if_not_exists`](if-not-exists-statement.md)<br/>
        [`__inline`](inline-functions-cpp.md)<sup>e</sup><br/>
        [`__int16`](int8-int16-int32-int64.md)<sup>e</sup><br/>
        [`__int32`](int8-int16-int32-int64.md)<sup>e</sup><br/>
        [`__int64`](int8-int16-int32-int64.md)<sup>e</sup><br/>
        [`__int8`](int8-int16-int32-int64.md)<sup>e</sup><br/>
        [`__interface`](interface.md)<br/>
        [`__leave`](try-finally-statement.md)<sup>e</sup><br/>
        [`__m128`](m128.md)<br/>
    :::column-end:::
    :::column:::
        [`__m128d`](m128d.md)<br/>
        [`__m128i`](m128i.md)<br/>
        [`__m64`](m64.md)<br/>
        [`__multiple_inheritance`](inheritance-keywords.md)<sup>e</sup><br/>
        [`__ptr32`](ptr32-ptr64.md)<sup>e</sup><br/>
        [`__ptr64`](ptr32-ptr64.md)<sup>Envoyer</sup><br/>
        [`__raise`](raise.md)<br/>
        [`__restrict`](extension-restrict.md)<sup>e</sup><br/>
        [`__single_inheritance`](inheritance-keywords.md)<sup>Envoyer</sup><br/>
        [`__sptr`](sptr-uptr.md)<sup>Envoyer</sup><br/>
        [`__stdcall`](stdcall.md)<sup>e</sup><br/>
    :::column-end:::
    :::column:::
        [`__super`](super.md)<br/>
        [`__thiscall`](thiscall.md)<br/>
        [`__unaligned`](unaligned.md)<sup>e</sup><br/>
        [`__unhook`](unhook.md)<sup>d</sup><br/>
        [`__uptr`](sptr-uptr.md)<sup>e</sup><br/>
        [`__uuidof`](uuidof-operator.md)<sup>e</sup><br/>
        [`__vectorcall`](vectorcall.md)<sup>e</sup><br/>
        [`__virtual_inheritance`](inheritance-keywords.md)<sup>e</sup><br/>
        [`__w64`](w64.md)<sup>e</sup><br/>
        [`__wchar_t`](fundamental-types-cpp.md)<br/>
    :::column-end:::
:::row-end:::

fonction intrinsèque <sup>d</sup> utilisée dans la gestion des événements.

<sup>e</sup> pour la compatibilité descendante avec les versions précédentes, ces mots clés sont disponibles à la fois avec deux traits de soulignement de début et un trait de soulignement simple lorsque les extensions Microsoft sont activées (valeur par défaut).

## <a name="microsoft-keywords-in-__declspec-modifiers"></a>Mots clés Microsoft dans les modificateurs __declspec

Ces identificateurs sont des attributs étendus pour le **`__declspec`** modificateur. Ils sont considérés comme des mots clés dans ce contexte.

:::row:::
    :::column:::
        [`align`](align-cpp.md)<br/>
        [`allocate`](allocate.md)<br/>
        [`allocator`](allocator.md)<br/>
        [`appdomain`](appdomain.md)<br/>
        [`code_seg`](code-seg-declspec.md)<br/>
        [`deprecated`](deprecated-cpp.md)
    :::column-end:::
    :::column:::
        [`dllexport`](dllexport-dllimport.md)<br/>
        [`dllimport`](dllexport-dllimport.md)<br/>
        [`jitintrinsic`](jitintrinsic.md)<br/>
        [`naked`](naked-cpp.md)<br/>
        [`noalias`](noalias.md)<br/>
        [`noinline`](noinline.md)
    :::column-end:::
    :::column:::
        [`noreturn`](noreturn.md)<br/>
        [`nothrow`](nothrow-cpp.md)<br/>
        [`novtable`](novtable.md)<br/>
        [`process`](process.md)<br/>
        [`property`](property-cpp.md)<br/>
        [`restrict`](restrict.md)
    :::column-end:::
    :::column:::
        [`safebuffers`](safebuffers.md)<br/>
        [`selectany`](selectany.md)<br/>
        [`spectre`](spectre.md)<br/>
        [`thread`](thread.md)<br/>
        [`uuid`](uuid-cpp.md)
    :::column-end:::
:::row-end:::

## <a name="ccli-and-ccx-keywords"></a>Mots clés c++/CLI et C++/CX

:::row:::
    :::column:::
        [`__abstract`](../dotnet/declaration-of-a-managed-class-type.md)<sup>f</sup><br/>
        [`__box`](../dotnet/value-type-semantics.md)<sup>f</sup><br/>
        [`__delegate`](../dotnet/delegates-and-events.md)<sup>f</sup><br/>
        [`__gc`](../dotnet/declaration-of-a-clr-reference-class-object.md)<sup>f</sup><br/>
        [`__identifier`](../extensions/identifier-cpp-cli.md)<br/>
        [`__nogc`](../dotnet/declaration-of-a-clr-reference-class-object.md)<sup>f</sup><br/>
        [`__noop`](../intrinsics/noop.md)<br/>
        **`__pin`**<sup>f</sup><br/>
        **`__property`**<sup>f</sup><br/>
        **`__sealed`**<sup>f</sup><br/>
    :::column-end:::
    :::column:::
        [`__try_cast`](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)<sup>f</sup><br/>
        [`__value`](../dotnet/value-type-semantics.md)<sup>f</sup><br/>
        [`abstract`](../extensions/abstract-cpp-component-extensions.md)<sup>g</sup><br/>
        [`array`](../extensions/arrays-cpp-component-extensions.md)<sup>g</sup><br/>
        [`as_friend`](../preprocessor/hash-using-directive-cpp.md)<br/>
        [`delegate`](../extensions/delegate-cpp-component-extensions.md)<sup>g</sup><br/>
        [`enum class`](../extensions/enum-class-cpp-component-extensions.md)<br/>
        [`enum struct`](../extensions/enum-class-cpp-component-extensions.md)<br/>
        [`event`](../extensions/event-cpp-component-extensions.md)<sup>g</sup><br/>
    :::column-end:::
    :::column:::
        [`finally`](../dotnet/finally.md)<br/>
        [`for each in`](../dotnet/for-each-in.md)<br/>
        [`gcnew`](../extensions/ref-new-gcnew-cpp-component-extensions.md)<sup>g</sup><br/>
        [`generic`](../extensions/generics-cpp-component-extensions.md)<sup>g</sup><br/>
        [`initonly`](../dotnet/initonly-cpp-cli.md)<br/>
        [`interface class`](../extensions/interface-class-cpp-component-extensions.md)<sup>g</sup><br/>
        [`interface struct`](../extensions/interface-class-cpp-component-extensions.md)<sup>g</sup><br/>
        [`interior_ptr`](../extensions/interior-ptr-cpp-cli.md)<sup>g</sup><br/>
        [`literal`](../extensions/literal-cpp-component-extensions.md)<sup>g</sup><br/>
    :::column-end:::
    :::column:::
        [`new`](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)<sup>g</sup><br/>
        [`property`](../extensions/property-cpp-component-extensions.md)<sup>g</sup><br/>
        [`ref class`](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
        [`ref struct`](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
        [`safecast`](../extensions/safe-cast-cpp-component-extensions.md)<br/>
        [`sealed`](../extensions/sealed-cpp-component-extensions.md)<sup>g</sup><br/>
        [`typeid`](../extensions/typeid-cpp-component-extensions.md)<br/>
        [`value class`](../extensions/classes-and-structs-cpp-component-extensions.md)<sup>g</sup><br/>
        [`value struct`](../extensions/classes-and-structs-cpp-component-extensions.md)<sup>g</sup><br/>
    :::column-end:::
:::row-end:::

<sup>f</sup> applicable uniquement aux extensions managées pour C++. Cette syntaxe est maintenant déconseillée. Pour plus d’informations, consultez [Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md).

<sup>f</sup> applicable à C++/CLI.

## <a name="see-also"></a>Voir aussi

[Conventions lexicales](lexical-conventions.md)<br/>
[Opérateurs, priorité et associativité C++ intégrés](cpp-built-in-operators-precedence-and-associativity.md)
