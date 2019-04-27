---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 682070877f269967405677d027b20707c8366f61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154955"
---
# <a name="comerrorsource"></a>_com_error::Source

**Section spécifique à Microsoft**

Appels `IErrorInfo::GetSource` (fonction).

## <a name="syntax"></a>Syntaxe

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetSource` pour le `IErrorInfo` objet enregistré dans le `_com_error` objet. Le `BSTR` résultant est encapsulé dans un objet `_bstr_t`. Si aucun `IErrorInfo` est enregistrée, elle retourne un vide `_bstr_t`.

## <a name="remarks"></a>Notes

Tout échec lors de l’appel la `IErrorInfo::GetSource` méthode est ignorée.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)