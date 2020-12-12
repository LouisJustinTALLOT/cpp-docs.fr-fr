---
description: 'En savoir plus sur : retval'
title: retval (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 15bfc994d18a9c61c37402aa763ecbfd96cbd768
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114856"
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

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|Paramètre d’interface, méthode d’interface|
|**Renouvelable**|Non|
|**Attributs requis**|**à**|
|**Attributs non valides**|**in**|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs de paramètre](parameter-attributes.md)<br/>
[Attributs de méthode](method-attributes.md)
