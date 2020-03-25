---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 775adfa7d5dd5aca098edcd793c2164d65fe7efa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190220"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Section spécifique de Microsoft**

Appelle `IErrorInfo::GetHelpFile` fonction.

## <a name="syntax"></a>Syntaxe

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetHelpFile` pour l’objet `IErrorInfo` enregistré dans l’objet `_com_error`. Le BSTR résultant est encapsulé dans un objet `_bstr_t`. Si aucune `IErrorInfo` n’est enregistrée, elle retourne un `_bstr_t`vide.

## <a name="remarks"></a>Notes

Tout échec lors de l’appel de la méthode `IErrorInfo::GetHelpFile` est ignoré.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
