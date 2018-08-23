---
title: Implements::fillarraywithiid, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c65e2d47d466b223acf19589e5966a05762605e3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611562"
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid, méthode

Insère l’ID d’interface spécifié par le paramètre de modèle actuel placée dans l’élément de tableau spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*  
Index de base zéro qui indique l’élément de tableau de départ pour cette opération. Lorsque cette opération se termine, *index* est incrémentée de 1.

*IID*  
Tableau de type IID.

## <a name="remarks"></a>Notes

Fonction d’assistance interne.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Implements, structure](../windows/implements-structure.md)