---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: cedb9ccadc63166c43d980333d93a195254700d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180704"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Section spécifique de Microsoft**

Récupère le `IErrorInfo` objet passé au constructeur.

## <a name="syntax"></a>Syntaxe

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

L'élément `IErrorInfo` brut est transmis dans le constructeur.

## <a name="remarks"></a>Notes

Récupère l’élément de `IErrorInfo` encapsulé dans un objet `_com_error`, ou NULL si aucun élément `IErrorInfo` n’est enregistré. L’appelant doit appeler `Release` sur l’objet retourné une fois qu’il a fini de l’utiliser.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)
