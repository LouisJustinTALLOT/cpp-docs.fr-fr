---
title: DeferrableEventArgs::GetDeferral (méthode) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47376a055da1625f718b7b2a8b6dbf4fe703e533
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601803"
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral (méthode)

Obtient une référence à la [report](http://go.microsoft.com/fwlink/p/?linkid=526520) objet qui représente un événement différé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```

### <a name="parameters"></a>Paramètres

*Résultat*  
Un pointeur qui référence le [report](http://go.microsoft.com/fwlink/p/?linkid=526520) lors de la fin de l’appel de l’objet.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="remarks"></a>Notes

Pour obtenir un exemple de code, consultez [deferrableeventargs, classe](../windows/deferrableeventargs-class.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[DeferrableEventArgs, classe](../windows/deferrableeventargs-class.md)