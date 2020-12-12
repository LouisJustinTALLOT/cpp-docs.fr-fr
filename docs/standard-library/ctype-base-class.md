---
description: 'En savoir plus sur : classe ctype_base'
title: ctype_base, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: 430e6fbf77842e61e662fd3024a54b418f487748
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324680"
---
# <a name="ctype_base-class"></a>ctype_base, classe

La classe sert de classe de base pour les facettes du modèle de classe [CType](../standard-library/ctype-class.md). Classe de base de la classe ctype utilisée pour définir des types énumération utilisés pour classifier ou tester les caractères, individuellement ou dans des plages entières.

## <a name="syntax"></a>Syntaxe

```cpp
struct ctype_base : public locale::facet
{
    enum
    {
        alnum,
        alpha,
        cntrl,
        digit,
        graph,
        lower,
        print,
        punct,
        space,
        upper,
        xdigit
    };
    typedef short mask;

    ctype_base( size_t _Refs = 0 );
    ~ctype_base();
};
```

## <a name="remarks"></a>Notes

Elle définit un masque d’énumération. Chaque constante d’énumération caractérise un autre moyen de classer des caractères, comme défini par les fonctions avec des noms similaires déclarés dans l’en-tête \<ctype.h> . Les constantes sont :

- **space** (fonction [isspace](../standard-library/locale-functions.md#isspace))

- **print** (fonction [isprint](../standard-library/locale-functions.md#isprint))

- **cntrl** (fonction [iscntrl](../standard-library/locale-functions.md#iscntrl))

- **upper** (fonction [isupper](../standard-library/locale-functions.md#isupper))

- **lower** (fonction [islower](../standard-library/locale-functions.md#islower))

- **digit** (fonction [isdigit](../standard-library/locale-functions.md#isdigit))

- **punct** (fonction [ispunct](../standard-library/locale-functions.md#ispunct))

- **xdigit** (fonction [isxdigit](../standard-library/locale-functions.md#isxdigit))

- **alpha** (fonction [isalpha](../standard-library/locale-functions.md#isalpha))

- **alnum** (fonction [isalnum](../standard-library/locale-functions.md#isalnum))

- **graph** (fonction [isgraph](../standard-library/locale-functions.md#isgraph))

Vous pouvez caractériser une combinaison de classifications en reliant ces constantes par une opération OR. En particulier, il est toujours vrai que **alnum** = = ( **alpha** &#124; **digit** \) et **Graph** \= \= \( **alnum** &#124; **punct**).

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
