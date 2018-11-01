---
title: ctype_base, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::ctype_base
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
ms.openlocfilehash: 83ef35f9fac438cfa217decf222abd365ff84269
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531129"
---
# <a name="ctypebase-class"></a>ctype_base, classe

La classe sert de classe de base pour les facettes de la classe de modèle [ctype](../standard-library/ctype-class.md). Classe de base de la classe ctype utilisée pour définir des types énumération utilisés pour classifier ou tester les caractères, individuellement ou dans des plages entières.

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

Elle définit un masque d’énumération. Chaque constante d’énumération caractérise une méthode de classification des caractères, comme défini par les fonctions avec des noms similaires déclarées dans l’en-tête \<ctype.h>. Les constantes sont :

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

Vous pouvez caractériser une combinaison de classifications en reliant ces constantes par une opération OR. En particulier, il est toujours true qui **alnum** == ( **alpha** &#124; **chiffre** \) et **graph** \= \= \( **alnum** &#124; **punct**).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
