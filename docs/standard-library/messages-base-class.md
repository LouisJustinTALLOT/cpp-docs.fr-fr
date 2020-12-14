---
description: 'En savoir plus sur : classe messages_base'
title: messages_base, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_base
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
ms.openlocfilehash: 45ea81b02bd15011c9f98b9364ea9918e248692a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230586"
---
# <a name="messages_base-class"></a>messages_base, classe

La classe de base décrit un **`int`** type pour le catalogue de messages.

## <a name="syntax"></a>Syntaxe

```cpp
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```

## <a name="remarks"></a>Notes

Le catalogue de types est un synonyme de type **`int`** qui décrit les valeurs de retour possibles de messages :: [do_open](../standard-library/messages-class.md#do_open).

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
