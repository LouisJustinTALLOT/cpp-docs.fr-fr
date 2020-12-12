---
description: 'En savoir plus sur : _com_error :: HelpContext'
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: 757fb572d9e41486af419712eb7f70cd7cfa7b14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295937"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Spécifique à Microsoft**

Appelle la `IErrorInfo::GetHelpContext` fonction.

## <a name="syntax"></a>Syntaxe

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetHelpContext` pour l' `IErrorInfo` objet enregistré dans l' `_com_error` objet. Si aucun `IErrorInfo` objet n’est enregistré, une valeur zéro est retournée.

## <a name="remarks"></a>Notes

Tout échec lors de l’appel de la `IErrorInfo::GetHelpContext` méthode est ignoré.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
