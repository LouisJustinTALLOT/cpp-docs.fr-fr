---
title: transmit_as | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.transmit_as
dev_langs:
- C++
helpviewer_keywords:
- transmit_as attribute
ms.assetid: 53d0b8ab-5b06-423e-83eb-3d01a10424b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32dec06fe458ceba26aaf9348d3fb12647a2a2ae
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593701"
---
# <a name="transmitas"></a>transmit_as

Indique au compilateur d’associer un type présenté qui manipulent des applications clientes et serveur, à un type transmis.

## <a name="syntax"></a>Syntaxe

```cpp
[ transmit_as(
   type
) ]
```

### <a name="parameters"></a>Paramètres

*type*  
Spécifie le type de données transmises entre le client et le serveur.

## <a name="remarks"></a>Notes

Le **transmit_as** attribut C++ a les mêmes fonctionnalités que le [transmit_as](http://msdn.microsoft.com/library/windows/desktop/aa367286) attribut MIDL.

## <a name="example"></a>Exemple

Le code suivant illustre une utilisation de la **transmit_as** attribut :

```cpp
// cpp_attr_ref_transmit_as.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[export] typedef struct _TREE_NODE_TYPE {
unsigned short data;
struct _TREE_NODE_TYPE * left;
struct _TREE_NODE_TYPE * right;
} TREE_NODE_TYPE;

[export] struct PACKED_NODE {
   unsigned short data;   // same as normal node
   int index;   // array index of parent
};

// A left node recursive built array of
// the nodes in the tree.  Can be unpacked with
// that knowledge
[export] typedef struct _TREE_XMIT_TYPE {
   int count;
   [size_is(count)] PACKED_NODE node[];
} TREE_XMIT_TYPE;

[transmit_as(TREE_XMIT_TYPE)] typedef TREE_NODE_TYPE * TREE_TYPE;
```

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**typedef**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="see-also"></a>Voir aussi

[Attributs IDL](../windows/idl-attributes.md)  
[Attributs Typedef, Enum, Union et Struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[export](../windows/export.md)  