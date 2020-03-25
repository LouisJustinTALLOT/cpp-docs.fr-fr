---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b5e884956b5a51d3c714f1a81dc6945409f74f4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180665"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Section spécifique de Microsoft**

Récupère le message de type chaîne pour HRESULT stocké dans l’objet `_com_error`.

## <a name="syntax"></a>Syntaxe

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le message de chaîne pour le HRESULT enregistré dans l’objet `_com_error`. Si le HRESULT est un [wCode](../cpp/com-error-wcode.md)16 bits mappé, un message générique «`IDispatch error #<wCode>`» est retourné. Si aucun message n'est trouvé, un message générique « `Unknown error #<hresult>` » est retourné. La chaîne retournée est une chaîne Unicode ou multioctets, selon l'état de la macro _UNICODE.

## <a name="remarks"></a>Notes

Récupère le texte de message système approprié pour HRESULT enregistré dans l’objet `_com_error`. Le texte du message système est obtenu en appelant la fonction Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) . La chaîne retournée est allouée par l’API `FormatMessage` et elle est libérée lorsque l’objet `_com_error` est détruit.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
