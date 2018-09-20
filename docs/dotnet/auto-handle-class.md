---
title: auto_handle, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_handle, msclr::auto_handle
- msclr.auto_handle
dev_langs:
- C++
helpviewer_keywords:
- auto_handle class
ms.assetid: a65604d1-ecbb-44fd-ae2f-696ddeeed9d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6509eaf8797d20303100c9886590bb2971e6c640
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419150"
---
# <a name="autohandle-class"></a>auto_handle, classe

Gestion automatique des ressources qui peut être utilisée pour incorporer un handle virtuel dans un type managé.

## <a name="syntax"></a>Syntaxe

```
template<typename _element_type>
ref class auto_handle;
```

#### <a name="parameters"></a>Paramètres

*_element_type*<br/>
Le type managé à incorporer.

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\auto_handle.h >

**Namespace** msclr

## <a name="see-also"></a>Voir aussi

[auto_handle](../dotnet/auto-handle.md)<br/>
[auto_handle, membres](../dotnet/auto-handle-members.md)<br/>
[auto_gcroot Class](../dotnet/auto-gcroot-class.md)