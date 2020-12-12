---
description: 'En savoir plus sur : _com_error :: source'
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 3b6cf35420454e8285d3d8b4deee3df8fe8771e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295768"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Spécifique à Microsoft**

Appelle la `IErrorInfo::GetSource` fonction.

## <a name="syntax"></a>Syntaxe

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetSource` pour l' `IErrorInfo` objet enregistré dans l' `_com_error` objet. Le `BSTR` résultant est encapsulé dans un objet `_bstr_t`. Si aucun `IErrorInfo` n’est enregistré, il retourne un vide `_bstr_t` .

## <a name="remarks"></a>Notes

Tout échec lors de l’appel de la `IErrorInfo::GetSource` méthode est ignoré.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
