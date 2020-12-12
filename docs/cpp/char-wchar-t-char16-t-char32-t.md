---
description: 'En savoir plus sur les éléments suivants : char, wchar_t, char16_t, char32_t'
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: f8bab56bf8a2cebe8409c9dc4ceecf931ec83260
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278790"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char, wchar_t, char16_t, char32_t

Les types **`char`** , **`wchar_t`** **`char16_t`** et **`char32_t`** sont des types intégrés qui représentent des caractères alphanumériques, ainsi que des glyphes non alphanumériques et des caractères non imprimables.

## <a name="syntax"></a>Syntaxe

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Notes

Le **`char`** type était le type de caractère d’origine en C et C++. Le type **`unsigned char`** est souvent utilisé pour représenter un *octet*, qui n’est pas un type intégré en C++. Le **`char`** type peut être utilisé pour stocker des caractères à partir du jeu de caractères ASCII ou de l’un des jeux de caractères ISO-8859, ainsi que des octets individuels de caractères multioctets tels que Shift-JIS ou l’encodage UTF-8 du jeu de caractères Unicode. Les chaînes de **`char`** type sont appelées chaînes *étroites* , même lorsqu’elles sont utilisées pour encoder des caractères multioctets. Dans le compilateur Microsoft, **`char`** est un type 8 bits.

Le **`wchar_t`** type est un type à caractères larges défini par l’implémentation. Dans le compilateur Microsoft, il représente un caractère étendu de 16 bits utilisé pour stocker le codage Unicode UTF-16LE, le type de caractère natif sur les systèmes d’exploitation Windows. Les versions à caractères larges des fonctions de la bibliothèque Runtime C universel (UCRT) utilisent **`wchar_t`** et leurs types pointeur et tableau en tant que paramètres et valeurs de retour, tout comme les versions à caractères larges de l’API Windows native.

Les **`char16_t`** **`char32_t`** types et représentent des caractères larges 16 bits et 32 bits, respectivement. L’encodage Unicode au format UTF-16 peut être stocké dans le type, et l’encodage Unicode au format **`char16_t`** UTF-32 peut être stocké dans le **`char32_t`** type. Les chaînes de ces types et **`wchar_t`** sont toutes appelées chaînes *larges* , bien que le terme fasse souvent référence spécifiquement à des chaînes de **`wchar_t`** type.

Dans la bibliothèque standard C++, le `basic_string` type est spécialisé pour les chaînes étroites et larges. Utilisez lorsque les caractères sont de type, lorsque les caractères sont de type, `std::string` **`char`** `std::u16string` **`char16_t`** `std::u32string` lorsque les caractères sont de type **`char32_t`** et `std::wstring` lorsque les caractères sont de type **`wchar_t`** . Les autres types qui représentent du texte, y compris `std::stringstream` et `std::cout` ont des spécialisations pour les chaînes étroites et larges.
