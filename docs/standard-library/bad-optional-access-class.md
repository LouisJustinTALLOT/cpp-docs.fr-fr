---
description: 'En savoir plus sur : classe bad_optional_access'
title: Classe bad_optional_access
ms.date: 08/06/2019
f1_keywords:
- optional/std::bad_optional_access
ms.openlocfilehash: e3439c53766a1890592bde8ed449f5ff2779f347
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132754"
---
# <a name="bad_optional_access-class"></a>Classe bad_optional_access

Définit le type des objets levés en tant qu’exceptions pour signaler la situation dans laquelle une tentative est faite pour accéder à la valeur d’un `optional` objet qui ne contient pas de valeur.

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

[\<optional>](optional.md)\
[optional, classe](optional-class.md)
