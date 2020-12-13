---
description: 'En savoir plus sur les éléments suivants : ODL'
title: ODL (attribut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.odl
helpviewer_keywords:
- odl attribute
ms.assetid: 75dcb314-b50f-4a63-9180-507ac1bc78f3
ms.openlocfilehash: 00228a11876a551a02a292fc4f20ea67f55506c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329733"
---
# <a name="odl"></a>odl

Identifie une interface en tant qu’interface ODL (Object Description Language). Le compilateur MIDL ne requiert pas l’attribut **ODL** ; Il est reconnu uniquement pour la compatibilité avec les anciens fichiers. ODL.

## <a name="syntax"></a>Syntaxe

```cpp
[odl]
```

## <a name="remarks"></a>Notes

L’attribut C++ **ODL** a les mêmes fonctionnalités que l’attribut MIDL [ODL](/windows/win32/Midl/odl) .

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_odl.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLIb")];

[odl, oleautomation, dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyInterface
{
   HRESULT x();
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
class cmyClass : public IMyInterface
{
public:
   HRESULT x(){}
};
```

## <a name="requirements"></a>Spécifications

| Contexte d’attribut | Valeur |
|-|-|
|**S’applique à**|**interface**|
|**Renouvelable**|Non|
|**Attributs requis**|None|
|**Attributs non valides**|None|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](idl-attributes.md)<br/>
[Attributs d’interface](interface-attributes.md)
