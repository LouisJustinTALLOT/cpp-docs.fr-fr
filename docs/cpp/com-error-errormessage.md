---
description: 'En savoir plus sur : _com_error :: ErrorMessage'
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: e7f91882d55e629744df5f26f7dcc64df1dddb22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296002"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Spécifique à Microsoft**

Récupère le message de type chaîne pour HRESULT stocké dans l' `_com_error` objet.

## <a name="syntax"></a>Syntaxe

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le message de chaîne pour le HRESULT enregistré dans l' `_com_error` objet. Si le HRESULT est un [wCode](../cpp/com-error-wcode.md)16 bits mappé, un message générique « `IDispatch error #<wCode>` » est retourné. Si aucun message n'est trouvé, un message générique « `Unknown error #<hresult>` » est retourné. La chaîne retournée est une chaîne Unicode ou multioctets, selon l'état de la macro _UNICODE.

## <a name="remarks"></a>Notes

Récupère le texte de message système approprié pour HRESULT enregistré dans l' `_com_error` objet. Le texte du message système est obtenu en appelant la fonction Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) . La chaîne retournée est allouée par l’API `FormatMessage` et elle est libérée lorsque l’objet `_com_error` est détruit.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
