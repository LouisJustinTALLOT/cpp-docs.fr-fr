---
description: 'En savoir plus sur : _com_error :: ErrorInfo'
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 36092ae9287352d421bf502ad24c054cf3b7a907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296041"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Spécifique à Microsoft**

Récupère l' `IErrorInfo` objet passé au constructeur.

## <a name="syntax"></a>Syntaxe

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

L'élément `IErrorInfo` brut est transmis dans le constructeur.

## <a name="remarks"></a>Notes

Récupère l' `IErrorInfo` élément encapsulé dans un `_com_error` objet, ou null si aucun `IErrorInfo` élément n’est enregistré. `Release`Lorsque vous avez fini de l’utiliser, l’appelant doit appeler sur l’objet retourné.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_error](../cpp/com-error-class.md)
