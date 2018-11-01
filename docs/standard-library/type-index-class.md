---
title: type_index, classe
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: 8807a041ab1c6ef47a9c3c12dac2688f121f6cfa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650489"
---
# <a name="typeindex-class"></a>type_index, classe

La classe `type_index` encapsule un pointeur dans la [classe type_info](../cpp/type-info-class.md) pour faciliter l’indexation par ces objets.

class type_index { public: type_index(const type_info& tinfo); const char *name() const; size_t hash_code() const; bool operator==(const type_info& right) const; bool operator!=(const type_info& right) const; bool operator<(const type_info& right) const; bool operator\<=(const type_info& right) const; bool operator>(const type_info& right) const; bool operator>=(const type_info& right) const; };

Le constructeur initialise `ptr` à `&tinfo`.

`name` retourne `ptr->name()`.

`hash_code` retourne « `ptr->hash_code().` »

`operator==` retourne `*ptr == right.ptr`.

`operator!=` retourne `!(*this == right)`.

`operator<` retourne `*ptr->before(*right.ptr)`.

`operator<=` retourne « `!(right < *this).` »

`operator>` retourne `right < *this`.

`operator>=` retourne `!(*this < right)`.

## <a name="see-also"></a>Voir aussi

[Informations de type au moment de l’exécution](../cpp/run-time-type-information.md)<br/>
[\<typeindex>](../standard-library/typeindex.md)<br/>
