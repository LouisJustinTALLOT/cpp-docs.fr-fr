---
title: HelpContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpcontext
dev_langs:
- C++
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5644f99e15685f8f1784cc40886709b05a9a06bd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221282"
---
# <a name="helpcontext"></a>helpcontext

Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le **aide** fichier.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpcontext(
   id
) ]
```

### <a name="parameters"></a>Paramètres

*ID*  
ID de contexte de la rubrique d’aide. Consultez [aide HTML : aide contextuelle pour vos programmes](../mfc/html-help-context-sensitive-help-for-your-programs.md) pour plus d’informations sur l’ID de contexte.

## <a name="remarks"></a>Notes

Le **helpcontext** attribut C++ a les mêmes fonctionnalités que le [helpcontext](/windows/desktop/Midl/helpcontext) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [defaultvalue](../windows/defaultvalue.md) pour obtenir un exemple montrant comment utiliser **helpcontext**.

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
[helpstring](../windows/helpstring.md)  