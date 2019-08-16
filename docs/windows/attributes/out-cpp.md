---
title: out (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 11c8e4473f0b849fab7846a825b90da3ed9f036f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514287"
---
# <a name="out-c"></a>out (C++)

Identifie des paramètres pointeurs qui sont retournés de la procédure appelée à la procédure appelante (du serveur au client).

## <a name="syntax"></a>Syntaxe

```cpp
[out]
```

## <a name="remarks"></a>Notes

L’attribut C++ **out** a les mêmes fonctionnalités que l’attribut MIDL [out](/windows/win32/Midl/out-idl) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [bindable](bindable.md) pour obtenir un exemple d’utilisation de **out**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun|
|**Attributs non valides**|Aucun|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)