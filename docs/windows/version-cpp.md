---
title: version (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a46a2f9b18a45e7ea627488881b0289e733ddd7b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608965"
---
# <a name="version-c"></a>version (C++)

Identifie une version particulière entre plusieurs versions d’une classe.

## <a name="syntax"></a>Syntaxe

```cpp
[ version(
   "version"
) ]
```

### <a name="parameters"></a>Paramètres

*version*  
Le numéro de version de la `coclass`. Si non spécifié, 1.0 sera placé dans le fichier .idl.

## <a name="remarks"></a>Notes

Le **version** attribut C++ a les mêmes fonctionnalités que le [version](http://msdn.microsoft.com/library/windows/desktop/aa367306) attribut MIDL et est transféré vers le fichier .idl généré.

## <a name="example"></a>Exemple

Consultez le [peut être liée](../windows/bindable.md) exemple pour un exemple d’utilisation de **version**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe**, **struct**|
|**Renouvelable**|Non|
|**Attributs requis**|**coclass**|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs de compilateur](../windows/compiler-attributes.md)  
[Attributs de classe](../windows/class-attributes.md)  