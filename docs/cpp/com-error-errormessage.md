---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b1c1b5a79cdf5ee2a4a17d969d23ce0d0d85ab54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504492"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage

**Section spécifique à Microsoft**

Récupère le message de type chaîne pour HRESULT stockées dans le `_com_error` objet.

## <a name="syntax"></a>Syntaxe

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Retourne le message de type chaîne pour la valeur HRESULT est enregistré dans le `_com_error` objet. Si la valeur HRESULT est 16 bits mappée [wCode](../cpp/com-error-wcode.md), puis un message générique «`IDispatch error #<wCode>`» est retournée. Si aucun message n'est trouvé, un message générique « `Unknown error #<hresult>` » est retourné. La chaîne retournée est soit une chaîne Unicode ou multioctets, selon l’état de la macro _UNICODE.

## <a name="remarks"></a>Notes

Récupère le texte du message système approprié pour le HRESULT est enregistré dans le `_com_error` objet. Le texte du message système est obtenu en appelant Win32 [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) (fonction). La chaîne retournée est allouée par l’API `FormatMessage` et elle est libérée lorsque l’objet `_com_error` est détruit.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)