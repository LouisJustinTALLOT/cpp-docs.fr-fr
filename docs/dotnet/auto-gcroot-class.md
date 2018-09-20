---
title: auto_gcroot, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48412a932ff3752b0613f7045cd88992332b7917
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423224"
---
# <a name="autogcroot-class"></a>auto_gcroot, classe

Gestion des ressources automatique (comme [auto_ptr, classe](../standard-library/auto-ptr-class.md)) qui peut être utilisé pour incorporer un handle virtuel dans un type natif.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename _element_type>
class auto_gcroot;
```

#### <a name="parameters"></a>Paramètres

*_element_type*<br/>
Le type managé à incorporer.

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>Voir aussi

[auto_gcroot](../dotnet/auto-gcroot.md)<br/>
[auto_gcroot Members](../dotnet/auto-gcroot-members.md)<br/>
[Guide pratique pour déclarer des handles dans les types natifs](../dotnet/how-to-declare-handles-in-native-types.md)<br/>
[auto_handle, classe](../dotnet/auto-handle-class.md)