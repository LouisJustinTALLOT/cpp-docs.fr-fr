---
description: 'En savoir plus sur : classe regex_error'
title: regex_error, classe
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: a6e2ace44c7463cbe43d000d3dabb9cf9f7d6676
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250502"
---
# <a name="regex_error-class"></a>regex_error, classe

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

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[code](#code)|Retourne le code d'erreur.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<regex>

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

## <a name="regex_errorcode"></a><a name="code"></a> regex_error :: code

Retourne le code d'erreur.

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la valeur passée au constructeur de l'objet.

## <a name="regex_errorregex_error"></a><a name="regex_error"></a> regex_error :: regex_error

Construit l’objet.

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>Paramètres

*Erreurs*\
Code d'erreur.

### <a name="remarks"></a>Notes

Le constructeur construit un objet qui contient la valeur *Error*.

## <a name="see-also"></a>Voir aussi

[\<regex>](../standard-library/regex.md)\
[Classe regex_constants](../standard-library/regex-constants-class.md)\
[\<regex> Mission](../standard-library/regex-functions.md)\
[Classe regex_iterator](../standard-library/regex-iterator-class.md)\
[\<regex> Operator](../standard-library/regex-operators.md)\
[Classe regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Classe regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
