---
description: 'En savoir plus sur les éléments suivants : oleautomation'
title: oleautomation (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 0227b1926d1e78f8f7bbfeb9b75ddd1b6d98aa2f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327420"
---
# <a name="oleautomation"></a>oleautomation

Indique qu’une interface est compatible avec Automation.

## <a name="syntax"></a>Syntaxe

```cpp
[oleautomation]
```

## <a name="remarks"></a>Notes

L’attribut C++ **oleautomation** a les mêmes fonctionnalités que l’attribut MIDL [oleautomation](/windows/win32/Midl/oleautomation) .

## <a name="example"></a>Exemple

Consultez les exemples pour [DefaultValue](defaultvalue.md) et [unextensible](nonextensible.md) pour obtenir un exemple d’utilisation de **oleautomation**.

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|**dispinterface**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
