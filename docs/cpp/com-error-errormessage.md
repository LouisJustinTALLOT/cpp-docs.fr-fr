---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: 44fc9755cd69050ea82145636f01614258943794
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500582"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Section spécifique à Microsoft**

Récupère le message de type chaîne pour HRESULT stocké `_com_error` dans l’objet.

## <a name="syntax"></a>Syntaxe

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le message de chaîne pour le HRESULT enregistré dans `_com_error` l’objet. Si le HRESULT est un [wCode](../cpp/com-error-wcode.md)16 bits mappé, un message générique «`IDispatch error #<wCode>`» est retourné. Si aucun message n'est trouvé, un message générique « `Unknown error #<hresult>` » est retourné. La chaîne retournée est une chaîne Unicode ou multioctets, selon l’état de la macro _ Unicode.

## <a name="remarks"></a>Notes

Récupère le texte de message système approprié pour HRESULT enregistré dans l' `_com_error` objet. Le texte du message système est obtenu en appelant la fonction Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) . La chaîne retournée est allouée par l’API `FormatMessage` et elle est libérée lorsque l’objet `_com_error` est détruit.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)