---
title: out (attribut de COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 7020bd6cfcf8bcdbfb773908e693c6364a29e343
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037579"
---
# <a name="out-c"></a>out (C++)

Identifie des paramètres pointeurs qui sont retournés de la procédure appelée à la procédure appelante (du serveur au client).

## <a name="syntax"></a>Syntaxe

```cpp
[out]
```

## <a name="remarks"></a>Notes

L’attribut C++ **out** a les mêmes fonctionnalités que l’attribut MIDL [out](/windows/desktop/Midl/out-idl) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [bindable](bindable.md) pour obtenir un exemple d’utilisation de **out**.

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[ID](id.md)