---
description: 'En savoir plus sur : _com_error :: HelpFile'
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: e45785913a8a5a1909f702bce672727171e0baef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295924"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Spécifique à Microsoft**

Appelle la `IErrorInfo::GetHelpFile` fonction.

## <a name="syntax"></a>Syntaxe

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetHelpFile` pour l' `IErrorInfo` objet enregistré dans l' `_com_error` objet. Le BSTR résultant est encapsulé dans un objet `_bstr_t`. Si aucun `IErrorInfo` n’est enregistré, il retourne un vide `_bstr_t` .

## <a name="remarks"></a>Notes

Tout échec lors de l’appel de la `IErrorInfo::GetHelpFile` méthode est ignoré.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
