---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 8e2c52d10b15822703329dcea18944773f5784ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180756"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Section spécifique de Microsoft**

Récupère le HRESULT passé au constructeur.

## <a name="syntax"></a>Syntaxe

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Élément HRESULT brut passé dans le constructeur.

## <a name="remarks"></a>Notes

Récupère l’élément HRESULT encapsulé dans un objet `_com_error`.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
