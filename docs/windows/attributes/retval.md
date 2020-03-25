---
title: retval (C++ attribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 5aded4588614eb4171e31a588f125ea8aa8de7ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166339"
---
# <a name="retval"></a>retval

Désigne le paramètre qui reçoit la valeur de retour du membre.

## <a name="syntax"></a>Syntaxe

```cpp
[retval]
```

## <a name="remarks"></a>Notes

L’attribut **retVal** C++ a les mêmes fonctionnalités que l’attribut MIDL [retVal](/windows/win32/Midl/retval) .

**retVal** doit apparaître sur le dernier argument dans la déclaration d’une fonction.

## <a name="example"></a>Exemple

Consultez l’exemple de [liaison](bindable.md) pour obtenir un exemple d’utilisation de **retVal**.

## <a name="requirements"></a>Spécifications

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|Paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|**out**|
|**Attributs non valides**|**in**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètres](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)
