---
description: 'En savoir plus sur : out (C++)'
title: out (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 1984d3bc539c5ad390cc1e507f2c8e3144d96ca2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329705"
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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Paramètre d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[DefaultValue](defaultvalue.md)<br/>
[id](id.md)
