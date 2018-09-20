---
title: HelpFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66cd89c28ea01c3a75d0cb25aa6f96a234e379b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418201"
---
# <a name="helpfile"></a>helpfile

Définit le nom du fichier d’aide pour une bibliothèque de types.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpfile(
   "filename"
) ]
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Le nom du fichier qui contient les rubriques d’aide.

## <a name="remarks"></a>Notes

Le **helpfile** attribut C++ a les mêmes fonctionnalités que le [helpfile](/windows/desktop/Midl/helpfile) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [module](../windows/module-cpp.md) pour obtenir un exemple montrant comment utiliser **helpfile**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**, **typedef**, **classe**, méthode, **propriété**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)<br/>
[Attributs d’interface](../windows/interface-attributes.md)<br/>
[Attributs de classe](../windows/class-attributes.md)<br/>
[Attributs de méthode](../windows/method-attributes.md)<br/>
[Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](../windows/helpcontext.md)<br/>
[helpstring](../windows/helpstring.md)  