---
description: 'En savoir plus sur : classe bad_array_new_length'
title: Classe bad_array_new_length
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_array_new_length
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: e9de10b6fee215651ac8ff6ce2fce4af55ce6c82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321638"
---
# <a name="bad_array_new_length-class"></a>Classe bad_array_new_length

La classe décrit une exception levée pour indiquer qu’une demande d’allocation n’a pas pu être effectuée en raison d’une taille de tableau inférieure à zéro ou supérieure à sa limite.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Notes

La valeur retournée par `what` est une chaîne C définie par l’implémentation. Aucune des fonctions membres ne lève d'exception.

## <a name="requirements"></a>Spécifications

**En-tête :**\<new>

## <a name="see-also"></a>Voir aussi

[Classe d’exception](../standard-library/exception-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
