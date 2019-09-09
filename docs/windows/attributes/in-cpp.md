---
title: in (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: e97008d0399764beeca73dbbc5914e4b891df748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514591"
---
# <a name="in-c"></a>in (C++)

Indique qu’un paramètre doit être passé de la procédure appelante à la procédure appelée.

## <a name="syntax"></a>Syntaxe

```cpp
[in]
```

## <a name="remarks"></a>Notes

L’attribut **in** C++ a les mêmes fonctionnalités que l’attribut MIDL [dans](/windows/win32/Midl/in) .

## <a name="example"></a>Exemple

Pour [obtenir un](bindable.md) exemple d’utilisation de **dans,** consultez.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|**retval**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)