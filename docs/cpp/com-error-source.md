---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 43dd21297ddd54863d535402dddd59243d589eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180522"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Section spécifique de Microsoft**

Appelle `IErrorInfo::GetSource` fonction.

## <a name="syntax"></a>Syntaxe

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetSource` pour l’objet `IErrorInfo` enregistré dans l’objet `_com_error`. Le `BSTR` résultant est encapsulé dans un objet `_bstr_t`. Si aucune `IErrorInfo` n’est enregistrée, elle retourne un `_bstr_t`vide.

## <a name="remarks"></a>Notes

Tout échec lors de l’appel de la méthode `IErrorInfo::GetSource` est ignoré.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
