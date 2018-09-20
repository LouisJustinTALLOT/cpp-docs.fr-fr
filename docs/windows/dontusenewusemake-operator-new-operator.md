---
title: DontUseNewUseMake::operator new, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99e82de06f64816521c47c78648108a9ae815279
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443226"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new, opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Paramètres

*__unnamed0*<br/>
Un paramètre sans nom qui spécifie le nombre d’octets de mémoire à allouer.

*sélection élective*<br/>
Le type doit être allouée.

## <a name="return-value"></a>Valeur de retour

Fournit un moyen de passer des arguments supplémentaires si vous surchargez l’opérateur **nouveau**.

## <a name="remarks"></a>Notes

Surcharge d’opérateur **nouveau** et empêche l’utilisation dans `RuntimeClass`.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[DontUseNewUseMake, classe](../windows/dontusenewusemake-class.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)