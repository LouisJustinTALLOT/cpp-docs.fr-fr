---
title: bad_optional_access, classe
ms.date: 08/06/2019
f1_keywords:
- optional/std::bad_optional_access
ms.openlocfilehash: 043b0360c7e0be48267c8f406dbfea50eeb5a8e3
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957097"
---
# <a name="bad_optional_access-class"></a>bad_optional_access, classe

Définit le type des objets levés en tant qu’exceptions pour signaler la situation dans laquelle une tentative est faite pour accéder `optional` à la valeur d’un objet qui ne contient pas de valeur.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_optional_access : public exception
{
public:
    bad_optional_access() noexcept;
    bad_optional_access(const bad_optional_access&) noexcept;
    bad_optional_access& operator=(const bad_optional_access&) noexcept;
    const char* what() const noexcept override;
};
```

## <a name="see-also"></a>Voir aussi

[\<> facultative](optional.md)\
[classe facultative](optional-class.md)
