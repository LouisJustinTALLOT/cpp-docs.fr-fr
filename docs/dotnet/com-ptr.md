---
title: com::ptr
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr
helpviewer_keywords:
- com::ptr
ms.assetid: ee302e3c-8fed-4875-a372-2e55003718d3
ms.openlocfilehash: 9bcfe00bd41d57542116f786f28df19d12c68b65
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664579"
---
# <a name="comptr"></a>com::ptr

Wrapper pour un objet COM qui peut être utilisé en tant que membre d’une classe CLR. Le wrapper automatise également la gestion de la durée de vie de l’objet COM à libérer les références détenues sur l’objet lorsque son destructeur est appelé. Analogue à [classe CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Syntaxe

```
#include <msclr\com\ptr.h>
```

## <a name="remarks"></a>Notes

[com::PTR, classe](../dotnet/com-ptr-class.md) est défini dans le \<msclr\com\ptr.h > fichier.

## <a name="see-also"></a>Voir aussi

[Bibliothèque de prise en charge C++](../dotnet/cpp-support-library.md)