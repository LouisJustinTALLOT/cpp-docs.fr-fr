---
title: system_error, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bde8e448d54be41516e65969f60b0651cacc8ef1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854556"
---
# <a name="systemerror-class"></a>system_error, classe

Représente la classe de base pour toutes les exceptions levées pour signaler une erreur système de bas niveau.

## <a name="syntax"></a>Syntaxe

```cpp
class system_error : public runtime_error {
public:
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

};
```

## <a name="remarks"></a>Notes

La valeur retournée par `what` dans la classe [exception](../standard-library/exception-class.md) est construite à partir de `_Message` et de l’objet stocké de type [error_code](../standard-library/error-code-class.md) (`code` ou `error_code(_Errval, _Errcat)`).

La fonction membre `code` retourne l’objet [error_code](../standard-library/error-code-class.md) stocké.

## <a name="requirements"></a>Spécifications

**En-tête :** \<system_error>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<system_error>](../standard-library/system-error.md)<br/>
