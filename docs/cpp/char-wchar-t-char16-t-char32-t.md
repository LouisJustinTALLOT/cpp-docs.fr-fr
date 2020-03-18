---
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: a518f24973aaddff59b97f104d9d912e4a2bedce
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447156"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char, wchar_t, char16_t, char32_t

Les types **char**, **wchar_t**, **char16_t** et **char32_t** sont des types intégrés qui représentent des caractères alphanumériques, ainsi que des glyphes non alphanumériques et des caractères non imprimables.

## <a name="syntax"></a>Syntaxe

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Notes

Le type **char** était le type de caractère d’origine en C++C et. Le type **unsigned char** est souvent utilisé pour représenter un *octet*, qui n’est pas un type intégré dans C++. Le type **char** peut être utilisé pour stocker des caractères à partir du jeu de caractères ASCII ou de l’un des jeux de caractères ISO-8859, ainsi que des octets individuels de caractères multioctets tels que Shift-JIS ou l’encodage UTF-8 du jeu de caractères Unicode. Les chaînes de type **char** sont appelées chaînes *étroites* , même lorsqu’elles sont utilisées pour encoder des caractères multioctets. Dans le compilateur Microsoft, **char** est un type 8 bits.

Le type de **wchar_t** est un type à caractères larges défini par l’implémentation. Dans le compilateur Microsoft, il représente un caractère étendu de 16 bits utilisé pour stocker le codage Unicode UTF-16LE, le type de caractère natif sur les systèmes d’exploitation Windows. Les versions à caractères larges des fonctions de la bibliothèque Runtime C universel (UCRT) utilisent **wchar_t** et ses types pointeur et tableau en tant que paramètres et valeurs de retour, tout comme les versions à caractères larges de l’API Windows native.

Les types **char16_t** et **char32_t** représentent respectivement des caractères larges 16 bits et 32 bits. L’encodage Unicode au format UTF-16 peut être stocké dans le type de **char16_t** , et le codage Unicode codé au format utf-32 peut être stocké dans le type de **char32_t** . Les chaînes de ces types et **wchar_t** sont toutes appelées chaînes *larges* , bien que le terme fasse souvent référence spécifiquement à des chaînes de type **wchar_t** .

Dans la C++ bibliothèque standard, le type de `basic_string` est spécialisé pour les chaînes étroites et larges. Utilisez `std::string` lorsque les caractères sont de type **char**, `std::u16string` quand les caractères sont de type **char16_t**, `std::u32string` quand les caractères sont de type **char32_t**, et `std::wstring` quand les caractères sont de type **wchar_t**. Les autres types qui représentent du texte, y compris `std::stringstream` et `std::cout` ont des spécialisations pour les chaînes étroites et larges.