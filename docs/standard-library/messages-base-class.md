---
title: messages_base, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_base
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
ms.openlocfilehash: 79b6cb5f0b0c219e959f53fdc667f4c8af273cef
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451847"
---
# <a name="messagesbase-class"></a>messages_base, classe

La classe de base décrit un type **int** pour le catalogue de messages.

## <a name="syntax"></a>Syntaxe

```cpp
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```

## <a name="remarks"></a>Notes

Le catalogue de types est un synonyme de type **int** qui décrit les valeurs de retour possibles de messages:: [do_open](../standard-library/messages-class.md#do_open).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
