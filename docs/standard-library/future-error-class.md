---
description: 'En savoir plus sur : classe future_error'
title: future_error, classe
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: c7dc99ea842cd13658c13a5c2492bda3d853302f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324211"
---
# <a name="future_error-class"></a>future_error, classe

Décrit un objet d’exception qui peut être levé par des méthodes dont les types gèrent les objets [future](../standard-library/future-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<future>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Classe logic_error](../standard-library/logic-error-class.md)\
[Classe error_code](../standard-library/error-code-class.md)
