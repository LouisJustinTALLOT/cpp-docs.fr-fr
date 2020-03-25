---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: de2275f096fe2fde96e64cbc3034602a1fde5e88
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180769"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Section spécifique de Microsoft**

Appelle `IErrorInfo::GetDescription` fonction.

## <a name="syntax"></a>Syntaxe

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetDescription` pour l’objet `IErrorInfo` enregistré dans l’objet `_com_error`. Le `BSTR` résultant est encapsulé dans un objet `_bstr_t`. Si aucune `IErrorInfo` n’est enregistrée, elle retourne un `_bstr_t`vide.

## <a name="remarks"></a>Notes

Appelle la fonction `IErrorInfo::GetDescription` et récupère les `IErrorInfo` enregistrées dans l’objet `_com_error`. Tout échec lors de l’appel de la méthode `IErrorInfo::GetDescription` est ignoré.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
