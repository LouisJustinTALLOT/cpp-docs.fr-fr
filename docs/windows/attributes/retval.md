---
title: retval (attribut de COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2b71271dc0579e1d0682b95a0d3bdf57d197d1a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790944"
---
# <a name="retval"></a>retval

Désigne le paramètre qui reçoit la valeur de retour du membre.

## <a name="syntax"></a>Syntaxe

```cpp
[retval]
```

## <a name="remarks"></a>Notes

Le **retval** attribut C++ a les mêmes fonctionnalités que le [retval](/windows/desktop/Midl/retval) attribut MIDL.

**retval** doit apparaître sur le dernier argument dans les déclaration d’une fonction.

## <a name="example"></a>Exemple

Consultez l’exemple de [peut être liée](bindable.md) pour un exemple d’utilisation de **retval**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|**out**|
|**Attributs non valides**|**in**|

Pour plus d’informations sur les contextes d’attribut, consultez [contextes d’attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)  