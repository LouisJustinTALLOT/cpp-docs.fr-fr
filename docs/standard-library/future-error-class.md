---
title: future_error, classe
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: 2b3f754c0ceb7384d99c6a657de214d30aca24b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159754"
---
# <a name="futureerror-class"></a>future_error, classe

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<future >

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[logic_error, classe](../standard-library/logic-error-class.md)<br/>
[error_code, classe](../standard-library/error-code-class.md)<br/>
