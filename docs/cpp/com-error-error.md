---
description: 'En savoir plus sur : _com_error :: Error'
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 25dd78caeada9e7606bc26f241126b0d0f510f4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318193"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Spécifique à Microsoft**

Récupère le HRESULT passé au constructeur.

## <a name="syntax"></a>Syntaxe

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Élément HRESULT brut passé dans le constructeur.

## <a name="remarks"></a>Notes

Récupère l’élément HRESULT encapsulé dans un `_com_error` objet.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
