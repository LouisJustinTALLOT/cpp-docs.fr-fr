---
title: Platform::recreateexception, méthode
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 9e167efc54352d125e849956a2da8d8e8cad4ed6
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693267"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException, méthode

Cette méthode est destinée à un usage interne uniquement et n'est pas destinée au code utilisateur. Utilisez la méthode Exception::CreateException à la place.

## <a name="syntax"></a>Syntaxe

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>Paramètres

*ressources humaines*

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Retourne un nouvel objet Platform::Exception^, basé sur le HRESULT spécifié.
