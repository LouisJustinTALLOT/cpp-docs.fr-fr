---
title: Platform::recreateexception, méthode | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
dev_langs:
- C++
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0472d74be21048aeaf25ca92dbb5c1e98ca0ca90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33087827"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException, méthode
Cette méthode est destinée à un usage interne uniquement et n'est pas destinée au code utilisateur. Utilisez la méthode Exception::CreateException à la place.

## <a name="syntax"></a>Syntaxe

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>Paramètres
`hr`

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Retourne un nouvel objet Platform::Exception^, basé sur le HRESULT spécifié.

