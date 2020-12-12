---
description: 'En savoir plus sur : dans (C++)'
title: in (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: c4d19fcf7adc767986306a3ef55b26a2cc91dccf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321374"
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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|**retval**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)<br/>
[DefaultValue](defaultvalue.md)<br/>
[id](id.md)<br/>
[à](out-cpp.md)
