---
title: HelpString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 928f4fe5200d9ea03541976664d472d9e99e1147
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575688"
---
# <a name="helpstring"></a>helpstring

Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstring(
   "string"
) ]
```

### <a name="parameters"></a>Paramètres

*string*  
Le texte de la chaîne d’aide.

## <a name="remarks"></a>Notes

Le **helpstring** attribut C++ a les mêmes fonctionnalités que le [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [defaultvalue](../windows/defaultvalue.md) pour obtenir un exemple montrant comment utiliser **helpstring**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **typedef**, **classe**, méthode, propriété|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs d’interface](../windows/interface-attributes.md)  
[Attributs de classe](../windows/class-attributes.md)  
[Attributs de méthode](../windows/method-attributes.md)  
[Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[helpfile](../windows/helpfile.md)  
[helpcontext](../windows/helpcontext.md)  