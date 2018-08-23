---
title: out (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.out
dev_langs:
- C++
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 220adeb44e676937756cf8007647f7e381f7607f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597558"
---
# <a name="out-c"></a>out (C++)

Identifie des paramètres pointeurs qui sont retournés de la procédure appelée à la procédure appelante (du serveur au client).

## <a name="syntax"></a>Syntaxe

```cpp
[out]
```

## <a name="remarks"></a>Notes

L’attribut C++ **out** a les mêmes fonctionnalités que l’attribut MIDL [out](http://msdn.microsoft.com/library/windows/desktop/aa367136) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [bindable](../windows/bindable.md) pour obtenir un exemple d’utilisation de **out**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs de paramètres](../windows/parameter-attributes.md)  
[defaultvalue](../windows/defaultvalue.md)  
[ID](../windows/id.md)  