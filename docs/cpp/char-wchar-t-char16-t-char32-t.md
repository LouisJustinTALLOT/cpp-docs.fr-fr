---
title: char, wchar_t, char16_t, char32_t | Documents Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
dev_langs:
- C++
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dc38eb9742459139747578a8227bdfaee8bb8a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="char-wchart-char16t-char32t"></a>char, wchar_t, char16_t, char32_t
Les types **char**, **wchar_t**, **char16_t** et **char32_t** sont des types intégrés qui représentent des caractères alphanumériques ainsi que glyphes non alphanumériques et des caractères non imprimables.

## <a name="syntax"></a>Syntaxe

```cpp  
char     ch1{ 'a' };  // or { u8'a' }   
wchar_t  ch2{ L'a' };    
char16_t ch3{ u'a' };    
char32_t ch4{ U'a' };  
```  
  
## <a name="remarks"></a>Notes

Le **char** type est le type de caractère d’origine en C et C++. Le type **unsigned char** est souvent utilisée pour représenter un *octets*, qui n’est pas un type intégré en C++. Le **char** type peut être utilisé pour stocker des caractères du jeu de caractères ASCII ou un des jeux de caractères ISO-8859 et des octets de caractères codés sur plusieurs octets tel que Shift-JIS ou l’encodage UTF-8 du jeu de caractères Unicode. Chaînes de **char** type sont appelés *limiter* des chaînes, même lorsque utilisé pour encoder des caractères multioctets. Dans le compilateur Microsoft, **char** est un type de 8 bits.

Le **wchar_t** type est un type défini par l’implémentation de caractères larges. Dans le compilateur Microsoft, il représente un caractère large 16 bits permet de stocker Unicode encodée au format UTF-16LE, le type de caractères natif sur les systèmes d’exploitation Windows. Les versions à caractères larges de l’utilisation de fonctions de bibliothèque Runtime C universel (UCRT) **wchar_t** et son pointeur et le tableau de types en tant que paramètres et valeurs de retour, comme les versions à caractères larges de l’API Windows native.

Le **char16_t** et **char32_t** représentent des types de caractères larges 16 bits et 32 bits, respectivement. Unicode encodé en UTF-16 peut être stockées dans le **char16_t** type et Unicode encodé en UTF-32 peut être stockées dans le **char32_t** type. Chaînes de ces types et **wchar_t** sont tous appelés *large* des chaînes, bien que le terme souvent fait référence spécifiquement pour les chaînes de **wchar_t** type.

Dans la bibliothèque C++ standard, le `basic_string` type est spécialisé pour les chaînes étroites et étendues. Utilisez `std::string` lorsque les caractères sont de type **char**, `std::u16string` lorsque les caractères sont de type **char16_t**, `std::u32string` lorsque les caractères sont de type **char32_t** , et `std::wstring` lorsque les caractères sont de type **wchar_t**. Autres types qui représentent le texte, y compris `std::stringstream` et `std::cout` ont des spécialisations pour les chaînes étroites et étendues.  
  
