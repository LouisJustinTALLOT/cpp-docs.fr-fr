---
title: regex_error, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: 52b6bfd74a08200f7d924d2601b85718a941dd85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451654"
---
# <a name="regexerror-class"></a>regex_error, classe

Signale un objet basic_regex incorrect.

## <a name="syntax"></a>Syntaxe

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Notes

Cette classe décrit un objet d’exception levé pour signaler une erreur dans la construction ou l’utilisation d’un objet `basic_regex` .

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[regex_error](#regex_error)|Construit l’objet.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[code](#code)|Retourne le code d'erreur.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<regex>

**Espace de noms :** std

## <a name="example"></a>Exemple

```cpp
// std__regex__regex_error.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }
```

```Output
regex error: unbalanced parentheses
```

## <a name="code"></a>  regex_error::code

Retourne le code d'erreur.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur passée au constructeur de l'objet.

## <a name="regex_error"></a>  regex_error::regex_error

Construit l’objet.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Paramètres

*Erreurs*\
Le code d’erreur.

### <a name="remarks"></a>Notes

Le constructeur construit un objet qui contient la valeur *Error*.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[regex_constants, classe](../standard-library/regex-constants-class.md)\
[\<fonctions Regex >](../standard-library/regex-functions.md)\
[regex_iterator, classe](../standard-library/regex-iterator-class.md)\
[\<opérateurs > Regex](../standard-library/regex-operators.md)\
[regex_token_iterator, classe](../standard-library/regex-token-iterator-class.md)\
[regex_traits, classe](../standard-library/regex-traits-class.md)\
[\<regex>, typedefs](../standard-library/regex-typedefs.md)
