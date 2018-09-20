---
title: com::PTR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr
dev_langs:
- C++
helpviewer_keywords:
- com::ptr
ms.assetid: ee302e3c-8fed-4875-a372-2e55003718d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f5e6a3f7936e21d22282fe37a29b5d91f2e50caa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434490"
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