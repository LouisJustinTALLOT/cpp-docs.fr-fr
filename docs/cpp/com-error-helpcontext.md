---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: a421a7fd7fa0817c74dac66946e28928b2ad82dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155083"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext

**Section spécifique à Microsoft**

Appels `IErrorInfo::GetHelpContext` (fonction).

## <a name="syntax"></a>Syntaxe

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetHelpContext` pour le `IErrorInfo` objet enregistré dans le `_com_error` objet. Si aucun `IErrorInfo` objet est enregistré, elle retourne un zéro.

## <a name="remarks"></a>Notes

Tout échec lors de l’appel la `IErrorInfo::GetHelpContext` méthode est ignorée.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)