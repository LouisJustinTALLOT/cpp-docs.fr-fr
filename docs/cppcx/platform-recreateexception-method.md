---
title: Platform::recreateexception, méthode
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 8173377a3d7a75bc85088037c229bac19f341649
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568868"
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
