---
title: retval (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: f90893390bc67cb495e646f61e3d61a994e42e50
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845989"
---
# <a name="retval"></a>retval

Désigne le paramètre qui reçoit la valeur de retour du membre.

## <a name="syntax"></a>Syntaxe

```cpp
[retval]
```

## <a name="remarks"></a>Notes

L’attribut C++ **retVal** a les mêmes fonctionnalités que l’attribut MIDL [retVal](/windows/win32/Midl/retval) .

**retVal** doit apparaître sur le dernier argument dans la déclaration d’une fonction.

## <a name="example"></a>Exemple

Consultez l’exemple de [liaison](bindable.md) pour obtenir un exemple d’utilisation de **retVal**.

## <a name="requirements"></a>Configuration requise

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Paramètre d’interface, méthode d’interface|
|**Repeatable Read**|Non|
|**Attributs requis**|**à**|
|**Attributs non valides**|**in**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)
