---
title: entrée (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 703a55ee7c56b64a5b168016770508508bab09e0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346131"
---
# <a name="entry"></a>entry

Spécifie une fonction exportée ou une constante dans un module en identifiant le point d’entrée dans la DLL.

## <a name="syntax"></a>Syntaxe

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
L’ID du point d’entrée.

## <a name="remarks"></a>Notes

Le **entrée** attribut C++ a les mêmes fonctionnalités que le [entrée](/windows/desktop/Midl/entry) attribut MIDL.

## <a name="example"></a>Exemple

Consultez l’exemple de [idl_module](idl-module.md) pour un exemple d’utilisation de **entrée**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|`idl_module` Attribut|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)