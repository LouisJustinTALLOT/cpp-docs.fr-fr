---
title: _com_error::source | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Source
dev_langs:
- C++
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69baf10012a461d60c6e7ae2d95a523ec725c255
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116540"
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