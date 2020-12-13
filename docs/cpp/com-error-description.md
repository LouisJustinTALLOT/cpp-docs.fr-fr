---
description: 'En savoir plus sur : _com_error ::D escription'
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: 6404d16361abe81d9e234a6b63039a7476d91ef1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332549"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Spécifique à Microsoft**

Appelle la `IErrorInfo::GetDescription` fonction.

## <a name="syntax"></a>Syntaxe

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Valeur de retour

Retourne le résultat de `IErrorInfo::GetDescription` pour l' `IErrorInfo` objet enregistré dans l' `_com_error` objet. Le `BSTR` résultant est encapsulé dans un objet `_bstr_t`. Si aucun `IErrorInfo` n’est enregistré, il retourne un vide `_bstr_t` .

## <a name="remarks"></a>Notes

Appelle la `IErrorInfo::GetDescription` fonction et récupère les `IErrorInfo` enregistrements dans l' `_com_error` objet. Tout échec lors de l’appel de la `IErrorInfo::GetDescription` méthode est ignoré.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
