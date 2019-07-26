---
title: bad_array_new_length, classe
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: b00042513364ac04b62ac7e1943d912dcb78f212
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459491"
---
# <a name="badarraynewlength-class"></a>bad_array_new_length, classe

La classe décrit une exception levée pour indiquer qu’une demande d’allocation n’a pas pu être effectuée en raison d’une taille de tableau inférieure à zéro ou supérieure à sa limite.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Notes

La valeur retournée `what` par est une chaîne C définie par l’implémentation. Aucune des fonctions membres ne lève d'exception.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<new>

## <a name="see-also"></a>Voir aussi

[Classe d’exception](../standard-library/exception-class.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
