---
description: 'En savoir plus sur : _com_error :: GUID'
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: 32f88728d5c0f93094413aaeae8fb3c116b415c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295963"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Spécifique à Microsoft**

Appelle la `IErrorInfo::GetGUID` fonction.

## <a name="syntax"></a>Syntaxe

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetGUID` pour l' `IErrorInfo` objet enregistré dans l' `_com_error` objet. Si aucun `IErrorInfo` objet n’est enregistré, il retourne `GUID_NULL` .

## <a name="remarks"></a>Notes

Tout échec lors de l’appel de la `IErrorInfo::GetGUID` méthode est ignoré.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
