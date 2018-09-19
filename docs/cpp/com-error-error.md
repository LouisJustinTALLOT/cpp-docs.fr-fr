---
title: _com_error::Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d56fcf7faaee9d3b0e02964163aa62372a30a78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109291"
---
# <a name="comerrorerror"></a>_com_error::Error

**Section spécifique à Microsoft**

Récupère la valeur HRESULT passé au constructeur.

## <a name="syntax"></a>Syntaxe

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Valeur de retour

Élément HRESULT brut passé au constructeur.

## <a name="remarks"></a>Notes

Récupère l’élément HRESULT encapsulé dans un `_com_error` objet.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_error, classe](../cpp/com-error-class.md)