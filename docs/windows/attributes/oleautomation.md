---
title: oleautomation (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 201916eeb235d48473d21188da42d19cafb93bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214662"
---
# <a name="oleautomation"></a>oleautomation

Indique qu’une interface est compatible avec Automation.

## <a name="syntax"></a>Syntaxe

```cpp
[oleautomation]
```

## <a name="remarks"></a>Notes

L’attribut **oleautomation** C++ a les mêmes fonctionnalités que l’attribut MIDL [oleautomation](/windows/win32/Midl/oleautomation) .

## <a name="example"></a>Exemple

Consultez les exemples pour [DefaultValue](defaultvalue.md) et [unextensible](nonextensible.md) pour obtenir un exemple d’utilisation de **oleautomation**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|**dispinterface**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
