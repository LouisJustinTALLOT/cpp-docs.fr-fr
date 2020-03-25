---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: b3c79bb069ef504680e83359d6ec90c803f16d9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180587"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Section spécifique de Microsoft**

Appelle `IErrorInfo::GetHelpContext` fonction.

## <a name="syntax"></a>Syntaxe

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetHelpContext` pour l’objet `IErrorInfo` enregistré dans l’objet `_com_error`. Si aucun objet `IErrorInfo` n’est enregistré, une valeur zéro est retournée.

## <a name="remarks"></a>Notes

Tout échec lors de l’appel de la méthode `IErrorInfo::GetHelpContext` est ignoré.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
