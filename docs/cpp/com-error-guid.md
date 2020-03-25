---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: d5b05cd4e26f89d42ea23b605f5e6560795a0cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180639"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Section spécifique de Microsoft**

Appelle `IErrorInfo::GetGUID` fonction.

## <a name="syntax"></a>Syntaxe

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetGUID` pour l’objet `IErrorInfo` enregistré dans l’objet `_com_error`. Si aucun objet `IErrorInfo` n’est enregistré, il retourne `GUID_NULL`.

## <a name="remarks"></a>Notes

Tout échec lors de l’appel de la méthode `IErrorInfo::GetGUID` est ignoré.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
