---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 59ada8a7e098e57cca5641a439365851bbae2485
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155070"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Section spécifique à Microsoft**

Récupère le `IErrorInfo` objet passé au constructeur.

## <a name="syntax"></a>Syntaxe

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

L'élément `IErrorInfo` brut est transmis dans le constructeur.

## <a name="remarks"></a>Notes

Récupère le texte encapsulé `IErrorInfo` d’éléments dans un `_com_error` de l’objet, ou NULL si aucun `IErrorInfo` élément est enregistré. L’appelant doit appeler `Release` sur l’objet retourné lors de la fin de l’utiliser.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)